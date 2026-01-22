# AAE5303 Environment Setup Report

> **Important:** Follow this structure exactly in your submission README.  
> Your goal is to demonstrate **evidence, process, problem-solving, and reflection** — not only screenshots.

---

## 1. System Information

**Laptop model:**  
_[Legion Y9000P]_

**CPU / RAM:**  
_[Intel(R) Core(TM) Ultra 9 275HX, 32GB RAM]_

**Host OS:**  
_[Windows 11]_

**Linux/ROS environment type:**  
_[Choose one:]_
- [ ] Dual-boot Ubuntu
- [ ] WSL2 Ubuntu
- [ ] Ubuntu in VM (UTM/VirtualBox/VMware/Parallels)
- [X] Docker container
- [ ] Lab PC
- [ ] Remote Linux server

---

## 2. Python Environment Check

### 2.1 Steps Taken

Describe briefly how you created/activated your Python environment:

Environment Setup Methodology:
  
  This project uses a Python virtual environment (venv) to isolate dependencies. The setup follows these steps:
  1. Virtual Environment Creation: Execute python3 -m venv .venv in the project root to create an isolated environment directory .venv.
  2. Environment Activation: Execute source .venv/bin/activate to activate the environment, ensuring subsequent commands use the Python interpreter and packages within this environment.
  3. Package Manager Upgrade: Execute python -m pip install --upgrade pip to upgrade pip to the latest version.
  4. Dependency Installation: Execute python -m pip install -r requirements.txt to install required packages (numpy≥2.0, scipy≥1.13, matplotlib≥3.8, opencv-python≥4.10, open3d==0.19.0).
Verification Results:
  After activation, all test scripts (test_python_env.py, test_open3d_pointcloud.py) passed, confirming the environment is correctly configured and ready for development and testing.

**Tool used:**  
_[venv]_

**Key commands you ran:**
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

**Any deviations from the default instructions:**  
_[None]_

### 2.2 Test Results

Run these commands and paste the actual terminal output (not just screenshots):

```bash
python scripts/test_python_env.py
```

**Output:**
```
[========================================
AAE5303 Environment Check (Python + ROS)
Goal: help you verify your environment and understand what each check means.
========================================

Step 1: Environment snapshot
  Why: We capture platform/Python/ROS variables to diagnose common setup mistakes (especially mixed ROS env).
Step 2: Python version
  Why: The course assumes Python 3.10+; older versions often break package wheels.
Step 3: Python imports (required/optional)
  Why: Imports verify packages are installed and compatible with your Python version.
Step 4: NumPy sanity checks
  Why: We run a small linear algebra operation so success means more than just `import numpy`.
Step 5: SciPy sanity checks
  Why: We run a small FFT to confirm SciPy is functional (not just installed).
Step 6: Matplotlib backend check
  Why: We generate a tiny plot image (headless) to confirm plotting works on your system.
Step 7: OpenCV PNG decoding (subprocess)
  Why: PNG decoding uses native code; we isolate it so corruption/codec issues cannot crash the whole report.
Step 8: Open3D basic geometry + I/O (subprocess)
  Why: Open3D is a native extension; ABI mismatches can segfault. Subprocess isolation turns crashes into readable failures.
Step 9: ROS toolchain checks
  Why: The course requires ROS tooling. This check passes if ROS 2 OR ROS 1 is available (either one is acceptable).
  Action: building ROS 2 workspace package `env_check_pkg` (this may take 1-3 minutes on first run)...
  Action: running ROS 2 talker/listener for a few seconds to verify messages flow...
Step 10: Basic CLI availability
  Why: We confirm core commands exist on PATH so students can run the same commands as in the labs.

=== Summary ===
✅ Environment: {
  "platform": "Linux-6.6.87.2-microsoft-standard-WSL2-x86_64-with-glibc2.35",
  "python": "3.10.12",
  "executable": "/root/PolyU-AAE5303-env-smork-test/.venv/bin/python",
  "cwd": "/root/PolyU-AAE5303-env-smork-test",
  "ros": {
    "ROS_VERSION": "2",
    "ROS_DISTRO": "humble",
    "ROS_ROOT": null,
    "ROS_PACKAGE_PATH": null,
    "AMENT_PREFIX_PATH": "/root/PolyU-AAE5303-env-smork-test/ros2_ws/install/env_check_pkg:/opt/ros/humble",
    "CMAKE_PREFIX_PATH": "/root/PolyU-AAE5303-env-smork-test/ros2_ws/install/env_check_pkg"
  }
}
✅ Python version OK: 3.10.12
✅ Module 'numpy' found (v2.2.6).
✅ Module 'scipy' found (v1.15.3).
✅ Module 'matplotlib' found (v3.10.8).
✅ Module 'cv2' found (v4.12.0).
✅ Module 'rclpy' found (vunknown).
✅ numpy matrix multiply OK.
✅ numpy version 2.2.6 detected.
✅ scipy FFT OK.
✅ scipy version 1.15.3 detected.
✅ matplotlib backend OK (Agg), version 3.10.8.
✅ OpenCV OK (v4.12.0), decoded sample image 128x128.
✅ Open3D OK (v0.19.0), NumPy 2.2.6.
✅ Open3D loaded sample PCD with 8 pts and completed round-trip I/O.
✅ ROS 2 CLI OK: /opt/ros/humble/bin/ros2
✅ ROS 1 tools not found (acceptable if ROS 2 is installed).
✅ colcon found: /usr/bin/colcon
✅ ROS 2 workspace build OK (env_check_pkg).
✅ ROS 2 runtime OK: talker and listener exchanged messages.
✅ Binary 'python3' found at /root/PolyU-AAE5303-env-smork-test/.venv/bin/python3

All checks passed. You are ready for AAE5303 🚀]
```

```bash
python scripts/test_open3d_pointcloud.py
```

**Output:**
```
[ℹ️ Loading /root/PolyU-AAE5303-env-smork-test/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /root/PolyU-AAE5303-env-smork-test/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.]
```

**Screenshot:**  
_[Include one screenshot showing both tests passing]_

<img width="1785" height="1403" alt="Python Test Passing" src="https://github.com/user-attachments/assets/ea95f0f5-9ff9-4d85-ae06-fa671340cbcc" />

---


## 3. ROS 2 Workspace Check

### 3.1 Build the workspace

Paste the build output summary (final lines only):

```bash
source /opt/ros/humble/setup.bash
colcon build
```

**Expected output:**
```
Summary: 1 package finished [x.xx s]
```

**Your actual output:**
```
[Starting >>> env_check_pkg
Finished <<< env_check_pkg [0.12s]

Summary: 1 package finished [0.38s]]
```

### 3.2 Run talker and listener

Show both source commands:

```bash
source /opt/ros/humble/setup.bash
source install/setup.bash
```

**Then run talker:**
```bash
ros2 run env_check_pkg talker.py
```

**Output (3–4 lines):**
```
[[INFO] [1768497998.904502226] [env_check_pkg_talker]: AAE5303 talker ready (publishing at 2 Hz).
[INFO] [1768497999.404653375] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #0'
[INFO] [1768497999.875614394] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #1'
[INFO] [1768498000.348411952] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #2']
```

**Run listener:**
```bash
ros2 run env_check_pkg listener.py
```

**Output (3–4 lines):**
```
[[INFO] [1768497979.743179487] [env_check_pkg_listener]: AAE5303 listener awaiting messages.
[INFO] [1768497979.891195835] [env_check_pkg_listener]: I heard: 'AAE5303 hello #24'
[INFO] [1768497980.252482710] [env_check_pkg_listener]: I heard: 'AAE5303 hello #25'
[INFO] [1768497980.725733843] [env_check_pkg_listener]: I heard: 'AAE5303 hello #26']
```

**Alternative (using launch file):**
```bash
ros2 launch env_check_pkg env_check.launch.py
```

**Screenshot:**  
_[Include one screenshot showing talker + listener running]_

Talker and Listener Running

<img width="1518" height="1304" alt="Talker and  Listener" src="https://github.com/user-attachments/assets/2cc5ed79-739f-49e0-a93a-0945d23d7681" />

---

## 4. Problems Encountered and How I Solved Them

> **Note:** Write 2–3 issues, even if small. This section is crucial — it demonstrates understanding and problem-solving.

### Issue 1: [ROS 2 environment not detected during smoke tests]

**Cause / diagnosis:**  
_[ROS 2 Humble was installed at /opt/ros/humble/, but the environment variables were not sourced in the current shell session. The test scripts check for ROS environment variables (ROS_VERSION, ROS_DISTRO, AMENT_PREFIX_PATH), which are only available after sourcing the ROS setup script.]_

**Fix:**  
_[Source the ROS 2 Humble setup script before running the smoke tests:]_

```bash
[source /opt/ros/humble/setup.bash
source .venv/bin/activate
python scripts/run_smoke_tests.py]
```

**Reference:**  
_[Project README.md troubleshooting section and ROS 2 Humble official documentation on environment setup.]_

---

### Issue 2: [Need to source workspace setup for ROS 2 package execution]

**Error message:**

_[When trying to run ROS 2 nodes directly, commands like ros2 run env_check_pkg talker may fail if the workspace is not properly sourced.]_

**Cause / diagnosis:**  
_[After building the ROS 2 workspace with colcon build, the built packages are installed to the install/ directory. To use these packages, the workspace setup script must be sourced to add the package paths to the environment.]_

**Fix:**  
_[Source both the ROS 2 base installation and the workspace installation:]_

```bash
[cd /root/PolyU-AAE5303-env-smork-test/ros2_ws
source /opt/ros/humble/setup.bash
source install/setup.bash
ros2 run env_check_pkg talker]
```

**Reference:**  
_[ROS 2 colcon workspace documentation and project README.md section on manual build and run.]_

---

## 5. Use of Generative AI (Required)

Choose one of the issues above and document how you used AI to solve it.

> **Goal:** Show critical use of AI, not blind copying.

### 5.1 Exact prompt you asked

**Your prompt:**
```
[I encountered an error when running the smoke tests, which indicated "ROS requirement not satisfied", but I know ROS 2 Humble is already installed on the system. What is the cause of this issue and how can I resolve it?]
```

### 5.2 Key helpful part of the AI's answer

**AI's response (relevant part only):**
```
[ROS 2 Humble is installed but not sourced. Source the ROS 2 environment first, then rerun the tests:

source /opt/ros/humble/setup.bash
source .venv/bin/activate
python scripts/run_smoke_tests.py]
```

### 5.3 What you changed or ignored and why

Explain briefly:
- Did the AI recommend something unsafe?
- Did you modify its solution?
- Did you double-check with official docs?

**Your explanation:**  
_[The AI's suggestion aligned with standard ROS 2 practices. I verified it by checking that /opt/ros/humble/ exists, confirming ROS 2 is installed. I then ran echo $ROS_VERSION in the shell, which returned empty, indicating the environment variables were not set. I cross-referenced the project README.md, which explicitly states that the ROS environment must be sourced before running tests. The AI's recommendation matched the official ROS 2 documentation and the project's own instructions, so no modification was needed. This is a common setup step that requires sourcing the ROS setup script in each new terminal session, and the AI correctly identified the root cause without suggesting any unsafe or unnecessary changes. Therefore, I applied the solution as recommended, which resolved the issue immediately upon execution.]_

### 5.4 Final solution you applied

Show the exact command or file edit that fixed the problem:

```bash
[cd /root/PolyU-AAE5303-env-smork-test
source /opt/ros/humble/setup.bash
source .venv/bin/activate
python scripts/run_smoke_tests.py]
```

**Why this worked:**  
_[source /opt/ros/humble/setup.bash sets the required ROS 2 environment variables (e.g., ROS_VERSION, ROS_DISTRO, AMENT_PREFIX_PATH), allowing the test scripts to detect the ROS 2 installation. After sourcing, the tests passed and the talker/listener functionality was verified. This is the standard way to use ROS 2 and must be executed in each new terminal session.]_

---

## 6. Reflection (3–5 sentences)

Short but thoughtful:

- What did you learn about configuring robotics environments?
- What surprised you?
- What would you do differently next time (backup, partitioning, reading error logs, asking better AI questions)?
- How confident do you feel about debugging ROS/Python issues now?

**Your reflection:**

  - Configuring robotics environments requires careful attention to environment variables and dependency management. I learned that ROS 2 requires explicit sourcing of setup scripts in each terminal session, which differs from typical        Python virtual environments.
  - What surprised me was how a missing source command could cause complete test failure even when ROS 2 was properly installed, highlighting the importance of understanding environment setup beyond just installation.
  - Next time, I would check environment variables first and document the exact sequence of source commands needed for reproducibility. 
  - After working through these issues, I feel more confident in debugging ROS/Python problems, as I now understand how ROS 2's workspace and base installation interact.]

---

## 7. Declaration

✅ **I confirm that I performed this setup myself and all screenshots/logs reflect my own environment.**

**Name:**  
_[HOU Guanhao]_

**Student ID:**  
_[25039773G]_

**Date:**  
_[17/01/2026]_

---

## Submission Checklist

Before submitting, ensure you have:

- [X] Filled in all system information
- [X] Included actual terminal outputs (not just screenshots)
- [X] Provided at least 2 screenshots (Python tests + ROS talker/listener)
- [X] Documented 2–3 real problems with solutions
- [X] Completed the AI usage section with exact prompts
- [X] Written a thoughtful reflection (3–5 sentences)
- [X] Signed the declaration

---

**End of Report**
