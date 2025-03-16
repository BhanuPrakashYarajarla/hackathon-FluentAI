# Installation Guide for FluentAI

Prerequisites:

Before installing the project, ensure you have the following dependencies installed:

-> Python 3.9+
-> pip (Python Package Manager)

-> Virtual Environment (venv)

-> Dlib Dependencies (for eye tracking)

-> OpenCV for image processing

-> Flask for web framework

->LanguageTool API for grammar checking

1. Clone the Repository

Open a terminal or command prompt and run:

git clone https://github.com/your-username/FluentAI.git

cd FluentAI

2. Setup Backend (Flask & AI Models)

Step 1: Create and Activate Virtual Environment

python -m venv venv

source venv/bin/activate  # On Windows use `venv\Scripts\activate`

Step 2: Install Dependencies

pip install -r requirements.txt

If you don’t have a requirements.txt file, create one with the following dependencies:

flask

opencv-python

dlib

numpy

requests

Then run:

pip install -r requirements.txt

Step 3: Download Dlib Pre-trained Model

Dlib requires a face landmark detection model. Download and extract it:

wget http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2 -- download the model from the link given here, because the model size is bigger to upload in github

bzip2 -d shape_predictor_68_face_landmarks.dat.bz2

mv shape_predictor_68_face_landmarks.dat backend/

Or manually download shape_predictor_68_face_landmarks.dat and place it in the backend/ directory.

3. Run the Backend Server

python main.py

By default, the backend will start at http://localhost:5000.

4. Testing the API

Check Grammar API

curl -X POST http://localhost:5000/check_grammar \
     -H "Content-Type: application/json" \
     -d '{"text": "This is a example with bad grammer."}'
     
Start Eye Tracking

curl -X POST http://localhost:5000/start_eye_tracking

Stop Eye Tracking

curl -X POST http://localhost:5000/stop_eye_tracking

5. Troubleshooting
   
If OpenCV/Dlib Installation Fails

Run the following based on your OS:

Linux/macOS:

sudo apt-get install cmake libopenblas-dev liblapack-dev libx11-dev

pip install dlib

Windows:

Install Visual Studio Build Tools

Run:

pip install cmake

pip install dlib
