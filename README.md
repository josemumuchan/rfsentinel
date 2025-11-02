# RF Sentinel 🛡️: Autonomous AFK Guardian for RF Online
<img width="1680" height="500" alt="RF Sentinel" src="https://github.com/user-attachments/assets/d1b06048-fb1c-43ce-a0e4-a523320abc21" /><br>
RF Sentinel is a companion tool made primarily for MAU users, developed with Claude AI, to protect your character during AFK farming sessions. Stop worrying about returning to a destroyed MAU. 

<br>
I developed this tool so I can fully go AFK without worrying that my MAU will be destroyed by raiders. 💥

# ✨ Core Protection Features

### 🤖 MAU Destruction Prevention 💥
Automatically monitors mounted health. If HP drops critically, the tool instantly triggers '**<ins>Take Off</ins>**' (dismount) to save your MAU from **destruction**.

https://github.com/user-attachments/assets/20a2e569-d18b-4738-a747-5beebb02e172

### 🧙‍♀️ F9 Key ❄️
Detects critical health and immediately uses the "**F9**" skill. I recommend using **<ins>Force Freezing</ins>** or other similar skills.

https://github.com/user-attachments/assets/b77625f9-67ff-41ba-ac88-ba3b4a227322

<br>

# 📑 How to Use (v1.0.0):
Remember to **<ins>run as administrator</ins>** since some RF Online clients are run as administrator and the app will not work if it is not run as administrator.

### ✅ Quick Start Guide

1. Launch RF Online and load your character
2. Open RF Sentinel
3. Select your game from dropdown
4. Wait for green ADDR: AUTO-RESOLVED message
5. Choose key method: **<ins>MAU or F9</ins>** (MAU is ON by default)
6. Adjust danger threshold slider **(optional)**
7. Press START when mounted
8. App monitors automatically - dismounts when HP drops

That's it! The app does the rest.

### 🤖 MAU mode
Login to character > select RF process > ride mau > START (make sure you are in **<ins>mouse mode</ins>**)

### 🧙‍♀️ F9 key mode
Login to character > select RF process > select "F9 Key" > START (make sure you are in **<ins>function keys mode</ins>**)<br>
<img width="488" height="59" alt="Screenshot 2025-11-02 144255" src="https://github.com/user-attachments/assets/81311ce7-fece-455e-b19c-6bb11919ed68" />

### 📒 Detailed Usage Guide:
1. Make sure you are already logged into your character.
2. Select RF Process from the dropdown menu:<br>
      <img width="240" height="127" alt="RF Sentinel v1 0 0 - 1" src="https://github.com/user-attachments/assets/d64ff306-b3bc-4625-a73e-ffd095271fe9" />
      <img width="240" height="127" alt="RF Sentinel v1 0 0- 2" src="https://github.com/user-attachments/assets/089d948b-a51e-4dd7-9e42-d595d5a14b59" />
3. 🤖 MAU Destruction Prevention 💥<br>
    - Ride your MAU. MAU mode is on by default.<br>
     <img width="240" height="347" alt="RF Sentinel v1 0 0- 3" src="https://github.com/user-attachments/assets/5ca3ea1f-acce-4d1f-a9fa-170beb804b36" />
     <img width="240" height="347" alt="RF Sentinel v1 0 0- 4" src="https://github.com/user-attachments/assets/65150b31-a04b-44fe-a11c-ee7c89c37e59" /><br>
    - Make sure you are on **<ins>mouse mode</ins>** since the app will be using the '/' key to dismount your MAU.<br><br>
4. 🧙‍♀️ F9 Key ❄️<br>
    - Make sure you are on **<ins>function key mode</ins>** since the app will be using the 'F9' key to use skill.<br>
   <img width="488" height="59" alt="Screenshot 2025-11-02 144255" src="https://github.com/user-attachments/assets/81311ce7-fece-455e-b19c-6bb11919ed68" />
   <br>
   <img width="240" height="248" alt="RF Sentinel v1 0 0- 5" src="https://github.com/user-attachments/assets/040ef3d7-affe-4212-86d6-e0590f45a933" /><br>
   <img width="240" height="347" alt="RF Sentinel v1 0 0- 6" src="https://github.com/user-attachments/assets/c85fb864-f5f5-40f1-9966-01f49ac8978e" />
   <img width="240" height="347" alt="RF Sentinel v1 0 0- 7" src="https://github.com/user-attachments/assets/9da471ff-1f6a-44bc-b911-6521aa19949e" /><br>
5. Optional: adjust threshold to your liking. Sentinel will activate when HP drops to threshold.

# 🪛 How It Works & Calibration

### 🛡️ RF Sentinel - Technical Process Flow

1. Process Selection: User selects RF Online client by PID from dropdown
2. Memory Connection: App attaches to game process using pymem library
3. HP Address Resolution (Auto):
    - Method 1 - Pointer Chain: Follow predefined memory path
    - Method 2 - AoB Scan (Fallback): Scan memory for signature if pointer fails
    - Store resolved address for monitoring
4. Configuration: User sets danger threshold (10-90%) and **unmount key mode** (MAU or F9)
5. Monitoring Start: User presses START button

    - Read current HP value from resolved address
    - Set as MAX HP baseline
    - Initialize monitoring loop (50ms intervals)

6. Continuous HP Monitoring Loop:

    - Read 4-byte signed integer from HP address
    - Calculate percentage: (Current HP / Max HP) × 100
    - Compare to threshold value
    - Update UI display every cycle

7. Threshold Breach Detection: If HP% ≤ Threshold% → Trigger key spam
8. Key Spam Execution Sequence:

    - Focus RF Online window
    - Update UI to danger state
    - Execute key spam loop (50 iterations):
        - MAU Mode: Send ESC → Send / → 25ms delay × 3
        - F9 Mode: Send F9 → 25ms delay × 2
    - Play system alert sound
    - Stop monitoring

9. Monitoring Stop: User presses STOP or key spam completes
    - Clear monitoring loop
    - Reset UI to idle state
    - Keep HP address in memory for restart

### 🪛 Calibration - Test Functions (Optional)
<img width="363" height="191" alt="RF Sentinel v1 0 0-mh" src="https://github.com/user-attachments/assets/9e8fa937-1c76-4c4a-bc12-6943fcae6174" /><br>
**AOB Button**:  <br>
Verify signature (AOB) scanning without connecting. Use this to check if HP address is getting scanned using AOB. Results will be in the 'rf_Sentinel_log.txt' file. <br><br>
**KEY Button**:  <br>
Execute key sequence. Monitoring needs to be active; START → KEY test

   <br><br><br>
*RF Sentinel was developed using AI-assisted scripting via Claude.ai*
