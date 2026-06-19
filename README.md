cd ~/orange_pi_deploy
sed -i 's/\r$//' setup_orangepi.sh record_video.sh
bash setup_orangepi.sh
source venv/bin/activate
pip install huggingface_hub requests
python download_models.py
python test_models.py



python -c "
from huggingface_hub import hf_hub_download
import shutil
from pathlib import Path

repo = 'abdulhadi111222/fyp-vehicle-models'
dest_dir = Path('models')
dest_dir.mkdir(exist_ok=True)

for f in ['efficientnet_b4_best.pth', 'classes.txt']:
    print(f'Downloading {f}...')
    cached = hf_hub_download(repo_id=repo, filename=f, force_download=True)
    shutil.copy2(cached, dest_dir / f)
    size = (dest_dir / f).stat().st_size
    print(f'  -> {size} bytes')
"
