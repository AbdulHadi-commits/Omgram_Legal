cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

echo 'export GATE_API_URL="https://automated-gate-access.vercel.app/api"' >> ~/.bashrc
echo 'export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"' >> ~/.bashrc
source ~/.bashrc

curl -s -X POST "$GATE_API_URL/gate/ingest" \
  -H "Content-Type: application/json" \
  -H "X-Gate-Token: $GATE_DEVICE_TOKEN" \
  -d '{"plate_texts":["TEST123"],"vehicle_label":"Toyota_Corolla","vehicle_conf":0.95,"preprocess_mode":"none"}'

  cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

python gate_sync.py --folder recordings/car_photos/ --preprocess auto


python3 << 'PYEOF'
from pathlib import Path

path = Path("gate_sync.py")
text = path.read_text()

old = '''def pil_to_data_url(pil_img: Image.Image) -> str:
    buf = io.BytesIO()
    pil_img.convert("RGB").save(buf, format="JPEG", quality=88)
    encoded = base64.b64encode(buf.getvalue()).decode("ascii")
    return f"data:image/jpeg;base64,{encoded}"'''

new = '''def pil_to_data_url(pil_img: Image.Image, max_side: int = 800, quality: int = 72) -> str:
    """Resize + compress so JSON payload stays under Vercel's ~4.5 MB limit."""
    img = pil_img.convert("RGB")
    w, h = img.size
    if max(w, h) > max_side:
        scale = max_side / max(w, h)
        img = img.resize((int(w * scale), int(h * scale)), Image.Resampling.LANCZOS)
    buf = io.BytesIO()
    img.save(buf, format="JPEG", quality=quality, optimize=True)
    raw = buf.getvalue()
    if len(raw) > 2_800_000:
        buf = io.BytesIO()
        img.save(buf, format="JPEG", quality=55, optimize=True)
        raw = buf.getvalue()
    encoded = base64.b64encode(raw).decode("ascii")
    return f"data:image/jpeg;base64,{encoded}"'''

if old not in text:
    print("Already patched or file changed — check gate_sync.py manually")
else:
    path.write_text(text.replace(old, new))
    print("Patched OK")



    
PYEOFaccess.vercel.app/api/gate/ingest
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
