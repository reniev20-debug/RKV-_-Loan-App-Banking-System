# OBS Studio Screen Recording Guide
## For Loan Approval AI Banking System Demo

**Installation Status:** ✅ Complete (OBS Studio 30.0.2)

---

## 🚀 How to Launch OBS Studio

### Option 1: Terminal Command
```bash
obs &
```

### Option 2: Applications Menu
- Click Activities/Show Applications
- Search for "OBS Studio"
- Click to launch

### Option 3: Desktop Shortcut
- Look for OBS Studio icon in your application launcher

---

## 📹 Step-by-Step Recording Instructions

### STEP 1: Launch OBS Studio
```bash
obs &
```
OBS will open with the main interface showing Sources, Scenes, and Recording controls.

### STEP 2: Set Up Your Scene

1. **Add Display Capture Source:**
   - In the Sources panel (bottom left), click the **+** button
   - Select **Display Capture** (or **Screen Capture**)
   - Choose your monitor
   - Click **Create New** → **OK**

2. **Verify Capture:**
   - Your screen should appear in the preview window
   - Resize if needed by dragging corners

### STEP 3: Configure Recording Settings

1. **Click Settings** (bottom right)
2. **Go to Output tab:**
   - **Output Mode:** Simple
   - **Recording Path:** `/home/ubuntu/Videos/` (or your preferred location)
   - **Recording Format:** MP4 (good for email/Teams)
   - **Recording Quality:** High/Very High
   - **Encoder:** Default

3. **Go to Video tab:**
   - **Base Canvas Resolution:** 1920x1080 (1080p) or 1280x720 (720p)
   - **Output Resolution:** Same as Base
   - **Common FPS Values:** 30 fps (standard)

4. **Apply and Close**

### STEP 4: Start Your Demo Recording

**Before Recording - Prepare Your Demo:**

1. **Open Terminal 1 - Start FastAPI Backend:**
```bash
cd "/home/ubuntu/Desktop/Capstone Project/Loan AI Banking App"
source venv/bin/activate
export PYTHONPATH="/home/ubuntu/Desktop/Capstone Project"
python -m uvicorn api:app --host 127.0.0.1 --port 8000
```
*(Keep this terminal running)*

2. **Open Terminal 2 - Start Streamlit Frontend:**
```bash
cd "/home/ubuntu/Desktop/Capstone Project/Loan AI Banking App"
source venv/bin/activate
export PYTHONPATH="/home/ubuntu/Desktop/Capstone Project"
streamlit run app.py
```
*(Keep this terminal running)*

3. **Wait for Streamlit to launch:**
```
You can now view your Streamlit app in your browser.

Local URL: http://localhost:8501
```

4. **Open Browser:**
- Navigate to `http://localhost:8501`
- Wait for the app to fully load

**Now Start Recording:**

1. In OBS, click the **Start Recording** button (red dot icon)
2. You should see "Recording" indicator in OBS

### STEP 5: Record Your Demo (5-10 minutes)

**Narrate and demonstrate:**

**Scenario 1: APPROVED Loan Application (2-3 min)**
```
Narration: "Let me show you the first scenario - an approved loan application."

1. Fill in the form:
   - Age: 38
   - Annual Income: $150,000
   - Employment: Full-time
   - Loan Amount: $200,000

2. Click "Submit Application"

3. Wait for analysis to complete (should be quick)

4. Show and explain the results:
   - Profile Analysis (Income Stability: High, Employment Risk: Low)
   - Risk Assessment (DTI Ratio: 1.33, Risk Level: Low)
   - Final Decision: APPROVED
   - Timestamp and Status

5. Click "View detailed results" expander to show JSON output
```

**Scenario 2: REJECTED Loan Application (2-3 min)**
```
Narration: "Now let's see a rejected application with high risk factors."

1. Click "Reset Form"

2. Fill in the form:
   - Age: 26
   - Annual Income: $35,000
   - Employment: Self-employed
   - Loan Amount: $300,000

3. Click "Submit Application"

4. Show and explain the results:
   - Profile Analysis (Income Stability: Low, Employment Risk: Medium)
   - Risk Assessment (DTI Ratio: 8.57, Risk Level: High)
   - Final Decision: REJECTED
   - Explain why: High DTI ratio and low income stability

5. Show detailed JSON output
```

**Scenario 3: REVIEW Loan Application (2-3 min)**
```
Narration: "Here's an application that requires manual review."

1. Click "Reset Form"

2. Fill in the form:
   - Age: 45
   - Annual Income: $65,000
   - Employment: Full-time
   - Loan Amount: $150,000

3. Click "Submit Application"

4. Show and explain the results:
   - Profile Analysis (Employment Risk: Low but Income: Moderate)
   - Risk Assessment (DTI Ratio: 2.31, Risk Level: High)
   - Final Decision: REVIEW
   - Explain: Manual review triggered due to risk factors

5. Show detailed analysis
```

**Optional: Show Backend/API (1-2 min)**
```
Narration: "Behind the scenes, this system uses:"

1. Show Streamlit frontend (currently visible)
2. Switch to Terminal 1 to show FastAPI logs
3. Explain the architecture:
   - Streamlit UI receives user input
   - FastAPI backend processes the request
   - LangGraph orchestrates the agent pipeline
   - Agents analyze and make decision
   - Result returned to frontend
```

### STEP 6: Stop Recording

1. In OBS, click the **Stop Recording** button
2. OBS will show "Recording Stopped"
3. Your video file will be saved to `/home/ubuntu/Videos/`

---

## 📁 Recording Output

**Default Location:** `/home/ubuntu/Videos/`

**File Format:** `obs_output_YYYY-MM-DD_HH-MM-SS.mp4`

**Check Recorded Files:**
```bash
ls -lh ~/Videos/
```

---

## 🎬 Recording Tips

### Audio Setup (Optional)
1. If you want to narrate:
   - Click **Audio Mixer** in OBS
   - Make sure your microphone is enabled
   - Test levels before recording

2. If no narration needed:
   - Keep audio muted for final submission
   - Or narrate after (easier for mistakes)

### Video Quality
- **720p (1280x720):** Good quality, smaller file size (~50-100 MB)
- **1080p (1920x1080):** Best quality, larger file size (~100-300 MB)
- **Both are acceptable for submission**

### Recording Length
- **Recommended:** 5-10 minutes
- **Minimum:** 3 minutes (show all 3 scenarios)
- **Maximum:** 15 minutes (keep it concise)

### File Size Estimation
- 1 minute at 720p: ~10-15 MB
- 5 minutes at 720p: ~50-75 MB
- 10 minutes at 720p: ~100-150 MB

**All sizes are suitable for email/Teams upload**

---

## ✅ Checklist Before Recording

- [ ] Both FastAPI and Streamlit are running
- [ ] Browser shows the Streamlit app at http://localhost:8501
- [ ] OBS is open and configured
- [ ] Display Capture source is added and visible in preview
- [ ] Recording path is set correctly
- [ ] Audio is configured (if narrating)
- [ ] Video resolution is set to 720p or 1080p
- [ ] FPS is set to 30
- [ ] You're ready to start demo

---

## 🎯 What to Demonstrate

**Show These Features:**

1. ✅ Loan application form with all inputs
2. ✅ Form validation and quick stats (DTI calculation)
3. ✅ Submit button and processing spinner
4. ✅ Results displayed with visual indicators (green for approved, red for rejected)
5. ✅ Profile analysis section
6. ✅ Risk assessment section
7. ✅ Final decision section with timestamp
8. ✅ Detailed results JSON expander
9. ✅ Multiple scenarios (Approved, Rejected, Review)
10. ✅ Professional UI/UX design

---

## 📝 Recording Script (Optional)

### Introduction (30 seconds)
```
"Good morning/afternoon. I'm Ritika Kaur Varshney, and this is the Loan 
Approval AI Banking System, an intelligent application for processing loan 
applications using AI agents. 

This system uses multiple specialized agents to analyze loan applications 
and make approval decisions. Let me walk you through a few scenarios."
```

### Scenario 1: Approved (2 min)
```
"Here's an application with strong financial profile. 
Age 38, annual income of $150,000, full-time employment, requesting $200,000 loan.

As you can see:
- Income stability: High
- Employment risk: Low
- DTI ratio: 1.33 (acceptable)
- Risk level: Low

Result: Application APPROVED

The system processed this through multiple agents - 
first evaluating the applicant profile, then analyzing financial risk,
then making the approval decision, and finally ensuring compliance."
```

### Scenario 2: Rejected (2 min)
```
"Now let's see a different outcome. This application has higher risk factors.
Age 26, annual income $35,000, self-employed, requesting $300,000 loan.

Analysis:
- Income stability: Low (lower income)
- Employment risk: Medium (self-employed)
- DTI ratio: 8.57 (way too high!)
- Risk level: High

Result: Application REJECTED

The high debt-to-income ratio exceeds acceptable limits, making this application 
not viable under current lending criteria."
```

### Scenario 3: Review (2 min)
```
"Finally, here's an application flagged for manual review.
Age 45, annual income $65,000, full-time employment, requesting $150,000 loan.

Analysis:
- Income stability: Moderate
- Employment risk: Low
- DTI ratio: 2.31 (concerning)
- Risk level: High

Result: REVIEW REQUIRED

This application meets some criteria but has risk factors that warrant 
manual review by a loan officer before making a final decision."
```

### Conclusion (30 seconds)
```
"The system provides clear, auditable decisions with detailed analysis at each step.
This combination of AI agents enables faster processing while maintaining compliance
and providing transparency in the lending decision process.

Thank you for watching."
```

---

## 🐛 Troubleshooting

### OBS Won't Start
```bash
# Try with verbose output:
obs --verbose
```

### Can't Record (Permission Denied)
```bash
# Create Videos directory:
mkdir -p ~/Videos
chmod 755 ~/Videos
```

### No Audio Input
1. Open OBS Settings
2. Go to Audio tab
3. Set Input Device to your microphone
4. Test levels

### Video Too Large/Small
1. Adjust Base Canvas Resolution in Settings
2. Restart OBS
3. Re-test recording

### FastAPI or Streamlit Won't Start
```bash
# Check if ports are in use:
lsof -i :8000  # FastAPI
lsof -i :8501  # Streamlit

# Kill if needed:
kill -9 <PID>
```

---

## 📤 After Recording

### Step 1: Locate Your Recording
```bash
ls -lh ~/Videos/ | grep -i obs
```

### Step 2: Verify the Video Works
```bash
# Play it to check quality:
vlc ~/Videos/obs_output_*.mp4
```

### Step 3: Rename for Clarity (Optional)
```bash
mv ~/Videos/obs_output_*.mp4 ~/Videos/Loan_App_Demo.mp4
```

### Step 4: Ready for Submission
```bash
# File is ready to upload to MS Teams
# Location: ~/Videos/Loan_App_Demo.mp4
```

---

## 📊 Quick Reference Commands

**Start Recording:**
```bash
# Terminal 1
cd "/home/ubuntu/Desktop/Capstone Project/Loan AI Banking App"
source venv/bin/activate
export PYTHONPATH="/home/ubuntu/Desktop/Capstone Project"
python -m uvicorn api:app --host 127.0.0.1 --port 8000

# Terminal 2
cd "/home/ubuntu/Desktop/Capstone Project/Loan AI Banking App"
source venv/bin/activate
export PYTHONPATH="/home/ubuntu/Desktop/Capstone Project"
streamlit run app.py

# Terminal 3
obs &
```

**View Recording:**
```bash
ls -lh ~/Videos/
vlc ~/Videos/obs_output_*.mp4
```

---

## ✅ Ready to Record?

Everything is set up! Follow these steps:

1. ✅ OBS Studio installed (v30.0.2)
2. ✅ Ensure FastAPI and Streamlit are running
3. ✅ Open OBS and add Display Capture source
4. ✅ Press Start Recording
5. ✅ Go through 3 scenarios (Approved, Rejected, Review)
6. ✅ Press Stop Recording
7. ✅ Verify video in ~/Videos/
8. ✅ Upload to MS Teams

---

**Good luck with your recording! 🎬**

For any issues, refer to this guide or the troubleshooting section above.
