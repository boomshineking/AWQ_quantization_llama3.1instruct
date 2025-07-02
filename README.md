# AWQ_quantization_llama3.1instruct 
From passing through a lot of hurdles from my previous project, I came to know bitsandbytes are not as compatible as AWQ model, so now i hard merged with Lora adaptors and then quantized the model using AWQ
 Contextual Bible Chatbot (LLaMA 3 Fine-Tuned)
 This project provides a simple yet powerful Bible Q&A chatbot powered by a 4-bit quantized and LoRA fine-tuned
 LLaMA 3.1-8B model. The chatbot provides answers to biblical questions and enriches responses with up to 3
 contextual verse explanations.
 Features- Context-aware answers based on user queries- Fine-tuned with LoRA adapters on Bible data- 4-bit quantization using GPTQ for fast inference- Easy-to-use Gradio web interface- Adds explanations for up to 3 Bible verses automatically
 Quick Start
 1. Clone the Repo
 ```bash
 git clone https://github.com/<your-username>/bible-llama3-chatbot.git
 cd bible-llama3-chatbot
 ```
 2. Install Dependencies
 ```bash
 pip install -r requirements.txt
 Or manually:
 ```bash
 pip install torch transformers peft auto-gptq gradio huggingface_hub
 ```
 3. Run the Demo
 ```bash
 python bible_chat_demo.py
 ```
 Model Details- 
 Base Model: meta-llama/Llama-3.1-8B-Instruct- LoRA Adapters: Richard9905/Lora_Bible_adaptors_forLLAMA3- 
 Merged Model: Merged_base_LLAMA3_bible-
 Quantized Version: Richard9905/4_bit_AWQ_Model
 Model Merging and Quantization Pipeline
 1. Load base LLaMA 3 model
 2. Apply LoRA Bible adapters
 3. Merge adapters using merge_and_unload()
 4. Quantize the model using auto-gptq (4-bit, group size 128)
 5. Save and push to Hugging Face Hub
 6. When the model detects certain verses like:- John 8:58- Genesis 1:1- John 3:16
 It appends an explanation like:
 Contextual Explanation for John 3:16:
 John 3:16 expresses God's love: "For God so loved the world, that he gave his only Son..."
 It highlights the offer of eternal life through faith.
 Only 3 verses maximum are attached per response.
 Hugging Face Authentication (Optional)
 To push models:
 ```bash
 huggingface-cli login
 ```
 Or set your token:
 ```bash
 export HF_TOKEN=your_token_here
 ```
 Project Structure- bible_chat_demo.py: Gradio demo UI- quantize_and_merge.py: Script for merging and quantizing model requirements.txt: Python dependencies- README.md: This file
 Future Improvements- Add streaming token output- Expand context DB with more verses- Deploy to GCP Vertex AI or Hugging Face Spaces- Improve RAG pipeline using FAISS
 Acknowledgements- Meta AI for LLaMA 3- Hugging Face for model hosting- Gradio for easy UI- auto-gptq for quantization
 License
 MIT Licens
