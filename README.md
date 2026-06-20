
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
cd ~/orange_pi_deploy
ls ~/orange_pi_deploy/recordings/car_photos/ | head -20
ls ~/orange_pi_deploy/recordings/car_photos/*.mp4
python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
for f in recordings/car_photos/*.mp4; do
  echo "Processing video: $f"
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 3
done






ading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.07, 'char_recognizer': 0.06, 'vmmr_classifier': 1.11}

Video: WIN_20260620_02_18_23_Pro.mp4 — sample every 28 frame(s)

Frame 0 (0.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : BQX-687
  Vehicle : Changan_Alsvin (82.8%)
  Weather : none (100% confidence)
            Clear: good contrast, low haze, no rain/night pattern
  Time    : 930 ms
  Website : event id 1 → closed

Frame 28 (1.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : BQX-687
  Vehicle : Changan_Alsvin (86.6%)
  Weather : none (69% confidence)
            Clear: good contrast, low haze, no rain/night pattern
  Time    : 735 ms
  Website : event id 1 → opened

Frame 56 (2.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : BQX-687
  Vehicle : Changan_Alsvin (66.9%)
  Weather : none (81% confidence)
            Clear: good contrast, low haze, no rain/night pattern
  Time    : 738 ms
  Website : event id 1 → closed

Frame 84 (3.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : BQX-687
  Vehicle : Changan_Alsvin (74.5%)
  Weather : none (81% confidence)
            Clear: good contrast, low haze, no rain/night pattern
  Time    : 736 ms
  Website : event id 2 → closed

Posted 4 event(s) to Live Feed
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.07, 'char_recognizer': 0.06, 'vmmr_classifier': 1.11}

Video: WIN_20260620_02_18_38_Pro.mp4 — sample every 28 frame(s)

Frame 0 (0.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LE-7550
  Vehicle : Suzuki_Mehran (26.5%)
  Weather : fog (58% confidence)
            Haze: sky haze 0.30, contrast 51.7
  Time    : 985 ms
  Website : event id 3 → closed

Frame 28 (1.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LE-5504
  Vehicle : Suzuki_Khyber (20.2%)
  Weather : fog (42% confidence)
            Haze: sky haze 0.17, contrast 64.3
  Time    : 841 ms
  Website : event id 4 → closed

Frame 56 (2.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEA-7550
  Vehicle : Suzuki_Mehran (16.4%)
  Weather : fog (33% confidence)
            Haze: sky haze 0.19, contrast 65.5
  Time    : 816 ms
  Website : event id 5 → closed

Frame 84 (3.0s)
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 310, in <module>
    raise SystemExit(main())
                     ^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 303, in main
    sync_video(Path(args.video), models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 195, in sync_video
    result = process_pil_image(pil, models, preprocess_mode=args.preprocess)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/pipeline.py", line 193, in process_pil_image
    return _run_pipeline_on_pil(
           ^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/pipeline.py", line 50, in _run_pipeline_on_pil
    wx = detect_weather_detailed(original)
         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/preprocessing.py", line 478, in detect_weather_detailed
    label, confidence, reason = _decide_weather(scores, features)
                                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/preprocessing.py", line 438, in _decide_weather
    sat < 88 and mb < 160,
    ^^^
NameError: name 'sat' is not defined. Did you mean: 'set'?
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.06, 'char_recognizer': 0.06, 'vmmr_classifier': 1.07}

Video: WIN_20260620_02_18_59_Pro.mp4 — sample every 28 frame(s)

Frame 0 (0.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : NO_PLATE_DETECTED
  Vehicle : Suzuki_Jimny 3rd Generation (16.5%)
  Weather : none (88% confidence)
            Clear: good contrast, low haze, no rain/night pattern
  Time    : 619 ms
  Website : event id 6 → closed

Frame 28 (1.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEH-8357
  Vehicle : Suzuki_Wagon R 1st Generation (77.3%)
  Weather : fog (52% confidence)
            Haze: sky haze 0.35, contrast 60.2
  Time    : 848 ms
  Website : event id 7 → closed

Frame 56 (2.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LE-8357
  Vehicle : Suzuki_Wagon R 1st Generation (84.2%)
  Weather : fog (39% confidence)
            Haze: sky haze 0.28, contrast 61.3
  Time    : 862 ms
  Website : event id 8 → closed

Frame 84 (3.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEH-8357
  Vehicle : Suzuki_Wagon R 1st Generation (92.5%)
  Weather : fog (39% confidence)
            Haze: sky haze 0.28, contrast 63.7
  Time    : 814 ms
  Website : event id 9 → opened

Frame 112 (4.0s)
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEH-8357
  Vehicle : Suzuki_Wagon R 1st Generation (85.1%)
  Weather : fog (60% confidence)
            Haze: sky haze 0.28, contrast 62.6
  Time    : 816 ms
  Website : event id 9 → opened

Posted 5 event(s) to Live Feed
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.07, 'char_recognizer': 0.06, 'vmmr_classifier': 1.11}

Syncing 48 image(s) to Live Feed

Pipeline: WIN_20260620_02_09_46_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : AAC-7396
  Vehicle : Toyota_yaris_gen 2018 2020 (56.2%)
  Weather : fog (60% confidence)
            Haze: sky haze 0.34, contrast 64.4
  Time    : 891 ms
  Website : event id 10 → closed

Pipeline: WIN_20260620_02_10_22_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : AAC-396
  Vehicle : Toyota_Corolla Axio 11th Generation (7.0%)
  Weather : fog (27% confidence)
            Haze: sky haze 0.19, contrast 65.9
  Time    : 818 ms
  Website : event id 11 → closed

Pipeline: WIN_20260620_02_11_00_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : BTY-8393
  Vehicle : Hyundai_Santro 2nd Generation (87.7%)
  Weather : none (88% confidence)
            Clear: good contrast, low haze, no rain/night pattern
  Time    : 773 ms
  Website : event id 12 → opened

Pipeline: WIN_20260620_02_11_12_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : AWC-049
  Vehicle : Honda_City 5th Generation (88.8%)
  Weather : fog (52% confidence)
            Haze: sky haze 0.29, contrast 70.3
  Time    : 738 ms
  Website : event id 13 → opened

Pipeline: WIN_20260620_02_11_54_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEC-3800
  Vehicle : Suzuki_Swift 1st Generation (91.9%)
  Weather : fog (46% confidence)
            Haze: sky haze 0.38, contrast 53.8
  Time    : 866 ms
  Website : event id 14 → opened

Pipeline: WIN_20260620_02_12_09_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEF-1392
  Vehicle : Suzuki_Cultus 3rd Generation (52.4%)
  Weather : fog (84% confidence)
            Haze: sky haze 0.26, contrast 50.0
  Time    : 900 ms
  Website : event id 15 → closed

Pipeline: WIN_20260620_02_12_19_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEE-9647
  Vehicle : Suzuki_Cultus 1st 2nd Generation (79.6%)
  Weather : fog (33% confidence)
            Haze: sky haze 0.18, contrast 68.3
  Time    : 793 ms
  Website : event id 16 → closed

Pipeline: WIN_20260620_02_12_33_Pro.jpg
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 310, in <module>
    raise SystemExit(main())
                     ^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 301, in main
    sync_folder(Path(args.folder), models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 161, in sync_folder
    if sync_image(img, models, args):
       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 140, in sync_image
    result = process_image(path, models, preprocess_mode=args.preprocess)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/pipeline.py", line 174, in process_image
    return _run_pipeline_on_pil(
           ^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/pipeline.py", line 50, in _run_pipeline_on_pil
    wx = detect_weather_detailed(original)
         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/preprocessing.py", line 478, in detect_weather_detailed
    label, confidence, reason = _decide_weather(scores, features)
                                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/preprocessing.py", line 438, in _decide_weather
    sat < 88 and mb < 160,
    ^^^
NameError: name 'sat' is not defined. Did you mean: 'set'?
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

