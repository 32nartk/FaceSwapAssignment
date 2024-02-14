# FaceSwapAssignment

git clone https://github.com/s0md3v/roop.git
cd roop
pip install -r requirements.txt
cd ..

wget https://huggingface.co/ezioruan/inswapper_128.onnx/resolve/main/inswapper_128.onnx -O inswapper_128.onnx
mkdir models
mv inswapper_128.onnx ./models

pip uninstall onnxruntime onnxruntime-gpu -y
pip install torch torchvision torchaudio --force-reinstall --index-url https://download.pytorch.org/whl/cu118
pip install onnxruntime-gpu

python /roop/run.py --target /demo_input.mp4  --source /demo_input.jpeg -o /demo_output.mp4 --execution-provider cuda --frame-processor face_swapper
