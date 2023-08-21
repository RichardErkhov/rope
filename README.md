# THIS IS NOT OFFICIAL REPOSITORY. ORIGINAL REPO WAS DELETED AND THE OWNER IS NOT ANSWERING
## anyway, thanks [hillobar](https://github.com/Hillobar) for creating rope, please answer to us, did someone kidnap you?
## Richard Discord link: [Discord](https://discord.gg/hzrJBGPpgN)
### The repo is not maintained, as Im developing my own tool, called [FastFaceSwap](https://github.com/RichardErkhov/FastFaceSwap) (actually rope was inspired by it, he told me). But I will help with troubleshooting if you have any issues.

#### I do not hape backup of images, sorry



# Rope
Rope implements the insightface inswapper_128 model with a helpful GUI.

### Features: ###
* Ugly GUI, but incredible features and fast workflow
* Fastest face swapper available
* Real-time video player
* Occlusion functions

### Changes for Rope - Space Worm: ###
* Updated video rendering to use Target Video parameters
* Mousewheel scroll on the time bar to control frame position
* Added an occluder model (experimental, very fast, make sure you download the new model-link below)
* Greatly increased performance for larger videos/multiple faces
* CLIP crashing fixed. Add as many words as you like!
* Detachable video preview
* Fixed most bugs related to changing options while playing. Adjust setting on the fly!
* GFPGAN now renders up to 512x512
* Status bar (still adding features to this)

### Known bugs: ### 
* Stop video playback before loading a new video, or bork

### Disclaimer: ###
Rope is a personal project that I'm making available to the community as a thank you for all of the contributors ahead of me. I don't have time to troubleshoot or add requested features, so it is provided as-is. Don't look at this code for example of good coding practices. I am primarily focused on performance and my specific use cases. There are plenty of ways to bork the workflow. Please see how to use below.

### Install: ###
Note: It's only configured for CUDA (Nvidia)
* Set up a local venv
  * python.exe -m venv venv
* Activate your new venv
  * .\venv\Scripts\activate
* Install requirements
  * .\venv\Scripts\pip.exe install -r .\requirements.txt
* Place [GFPGANv1.4.onnx](https://github.com/RichardErkhov/rope/releases/download/models/GFPGANv1.4.onnx), [inswapper_128_fp16.onnx](https://github.com/RichardErkhov/rope/releases/download/models/inswapper_128.fp16.onnx), and [occluder.ckpt](https://github.com/RichardErkhov/rope/releases/download/models/occluder.ckpt) in the `weights/` directory
* Do this if you've never installed roop or Rope (or any other onnx runtimes):
  * Install CUDA Toolkit 11.8
  * Install dependencies:
  * pip uninstall onnxruntime onnxruntime-gpu
  * pip install onnxruntime-gpu==1.15.1
* Double-click on Rope.bat!

### To use: ###
* Run Rope.bat
* Set your Target Video, Source Faces, and Video Output folders
  * Buttons will be gold if they are not set
  * Only places videos or images in the respective folders. Other files my bork it
  * Rope creates a JSON file to remember your last set paths
  * I like to keep my folders <20 or so items. Helps to organize and reduces load times
* Click on the Load Models button to initialize Rope
* Select a video to load it into the player
* Find Target Faces
  * Adds all faces in the current frame to the Found Faces pane
  * If a Face is already Found and in the pane, it won't re-add it
* Click a Source Face
  * Source Face number will appear
* Select a Target Face
  * Target Faces will show assignment number to the Source Face number
  * Toggle a Target Face to unselect and reassign to currently selected Source Face
* Continue to select other Source Faces and assign them to Target Faces
* Click SWAP to enable face swapping
* Click PLAY to play
* Click REC to arm recording
  * Click PLAY to start recording using the current settings
  * Click PLAY again to stop recording, otherwise it will record to the end of the Target Video
* Toggle GFPGAN, adjust blending amount
* Toggle Diffing, adjust blending amount
* Lower the threshhold if you have multiple Source Faces assigned and they are jumping around. You can also try Clearing and Finding new Target Faces (disable SWAP first)
* Modify the Masking boundaries
* Use CLIP to identify objects to swap or not swap (e.g Pos: face, head; Neg: hair, hand), adjust the gain of the words, and set the blur amount around the items
* Change # threads to match your GPU memory (24GB ~9 threads with GFPGAN on, more threads w/o GFPGAN)
  * Start with the lowest you think will run and watch your GPU memory.
  * Once you allocate memory by increasing # threads, you can't un-allocate it by reducing # threads. You will need to restart Rope.
* In general, always stop the video before changing anything. Otherwise, it might bork. Reassigning faces is okay
* If it does bork, reload the video (reclick on it). If that doesn't work you'll need to restart
  
