cd ~/orange_pi_deploy
sed -i 's/\r$//' setup_orangepi.sh record_video.sh
bash setup_orangepi.sh
source venv/bin/activate
pip install huggingface_hub requests
python download_models.py
python test_models.py




hadi@hadi-desktop:~$ cd ~/orange_pi_deploy
hadi@hadi-desktop:~/orange_pi_deploy$ python test_models.py
Command 'python' not found, did you mean:
  command 'python3' from deb python3
  command 'python' from deb python-is-python3
hadi@hadi-desktop:~/orange_pi_deploy$ venv/bin/activate 
bash: venv/bin/activate: Permission denied
hadi@hadi-desktop:~/orange_pi_deploy$ source venv/bin/activate
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python test_models.py
Loading all models...
/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/torch/nn/modules/linear.py:124: UserWarning: Initializing zero-element tensors is a no-op
  init.kaiming_uniform_(self.weight, a=math.sqrt(5))
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/test_models.py", line 56, in <module>
    main()
  File "/home/hadi/orange_pi_deploy/test_models.py", line 18, in main
    models = load_all_models()
             ^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/models_loader.py", line 93, in load_all_models
    vehicle_model, vehicle_classes, vehicle_transform = _load_vehicle_classifier(device)
                                                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/models_loader.py", line 54, in _load_vehicle_classifier
    checkpoint = torch.load(VMMR_CHECKPOINT_PATH, map_location="cpu", weights_only=False)
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
           ^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
EOFError: Ran out of input
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ te pip install huggingface_hub requests
te: command not found
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ pip install huggingface_hub requests
Requirement already satisfied: huggingface_hub in ./venv/lib/python3.12/site-packages (1.20.1)
Requirement already satisfied: requests in ./venv/lib/python3.12/site-packages (2.34.2)
Requirement already satisfied: click>=8.4.0 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (8.4.1)
Requirement already satisfied: filelock>=3.10.0 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (3.29.0)
Requirement already satisfied: fsspec>=2023.5.0 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (2026.4.0)
Requirement already satisfied: hf-xet<2.0.0,>=1.5.1 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (1.5.1)
Requirement already satisfied: httpx<1,>=0.23.0 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (0.28.1)
Requirement already satisfied: packaging>=20.9 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (26.2)
Requirement already satisfied: pyyaml>=5.1 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (6.0.3)
Requirement already satisfied: tqdm>=4.42.1 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (4.68.3)
Requirement already satisfied: typer<0.26.0,>=0.20.0 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (0.25.1)
Requirement already satisfied: typing-extensions>=4.1.0 in ./venv/lib/python3.12/site-packages (from huggingface_hub) (4.15.0)
Requirement already satisfied: anyio in ./venv/lib/python3.12/site-packages (from httpx<1,>=0.23.0->huggingface_hub) (4.14.0)
Requirement already satisfied: certifi in ./venv/lib/python3.12/site-packages (from httpx<1,>=0.23.0->huggingface_hub) (2026.6.17)
Requirement already satisfied: httpcore==1.* in ./venv/lib/python3.12/site-packages (from httpx<1,>=0.23.0->huggingface_hub) (1.0.9)
Requirement already satisfied: idna in ./venv/lib/python3.12/site-packages (from httpx<1,>=0.23.0->huggingface_hub) (3.18)
Requirement already satisfied: h11>=0.16 in ./venv/lib/python3.12/site-packages (from httpcore==1.*->httpx<1,>=0.23.0->huggingface_hub) (0.16.0)
Requirement already satisfied: shellingham>=1.3.0 in ./venv/lib/python3.12/site-packages (from typer<0.26.0,>=0.20.0->huggingface_hub) (1.5.4)
Requirement already satisfied: rich>=13.8.0 in ./venv/lib/python3.12/site-packages (from typer<0.26.0,>=0.20.0->huggingface_hub) (15.0.0)
Requirement already satisfied: annotated-doc>=0.0.2 in ./venv/lib/python3.12/site-packages (from typer<0.26.0,>=0.20.0->huggingface_hub) (0.0.4)
Requirement already satisfied: charset_normalizer<4,>=2 in ./venv/lib/python3.12/site-packages (from requests) (3.4.7)
Requirement already satisfied: urllib3<3,>=1.26 in ./venv/lib/python3.12/site-packages (from requests) (2.7.0)
Requirement already satisfied: markdown-it-py>=2.2.0 in ./venv/lib/python3.12/site-packages (from rich>=13.8.0->typer<0.26.0,>=0.20.0->huggingface_hub) (4.2.0)
Requirement already satisfied: pygments<3.0.0,>=2.13.0 in ./venv/lib/python3.12/site-packages (from rich>=13.8.0->typer<0.26.0,>=0.20.0->huggingface_hub) (2.20.0)
Requirement already satisfied: mdurl~=0.1 in ./venv/lib/python3.12/site-packages (from markdown-it-py>=2.2.0->rich>=13.8.0->typer<0.26.0,>=0.20.0->huggingface_hub) (0.1.2)
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python download_models.py 
Downloading from https://huggingface.co/abdulhadi111222/fyp-vehicle-models
Into: /home/hadi/orange_pi_deploy/models

  skip  plate_best.pt (already exists)
  skip  char_best.pt (already exists)
  skip  efficientnet_b4_best.pth (already exists)
  skip  classes.txt (already exists)

All models ready. Run: python test_models.py
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python test_models.py
Loading all models...
/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/torch/nn/modules/linear.py:124: UserWarning: Initializing zero-element tensors is a no-op
  init.kaiming_uniform_(self.weight, a=math.sqrt(5))
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/test_models.py", line 56, in <module>
    main()
  File "/home/hadi/orange_pi_deploy/test_models.py", line 18, in main
    models = load_all_models()
             ^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/models_loader.py", line 93, in load_all_models
    vehicle_model, vehicle_classes, vehicle_transform = _load_vehicle_classifier(device)
                                                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/models_loader.py", line 54, in _load_vehicle_classifier
    checkpoint = torch.load(VMMR_CHECKPOINT_PATH, map_location="cpu", weights_only=False)
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
           ^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
EOFError: Ran out of input
