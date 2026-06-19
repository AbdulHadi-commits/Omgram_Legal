cd ~/orange_pi_deploy
sed -i 's/\r$//' setup_orangepi.sh record_video.sh
bash setup_orangepi.sh
source venv/bin/activate
pip install huggingface_hub requests
python download_models.py
python test_models.py



rm models/efficientnet_b4_best.pth models/classes.txt
