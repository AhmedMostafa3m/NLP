![tape image]https://github.com/AhmedMostafa3m/NLP/blob/96e9fb5970ae673f9e056bc537f284c631934f88/dataset_generator/egypt_dataset%20-%20Trim.mp4
🚀 Building a Smart Dataset Generator with LLaMA and Gradio!

I recently worked on a mini-project that combines the power of Meta’s LLaMA 3.2–1B Instruct, quantization with BitsAndBytes, and an interactive Gradio interface — all to generate educational datasets automatically.

The app allows users to:

Choose a topic

Provide a few sample inquiry–response pairs

Instantly generate a complete JSON-formatted dataset with consistent style and clarity

I used 4-bit quantization (NF4) to reduce GPU memory usage, making the model lightweight yet efficient.

Here’s the core logic behind it 👇
(simplified for readability)

# Load quantized LLaMA model
def load_model(model_name):
    quant_config = BitsAndBytesConfig(
        load_in_4bit=True,
        bnb_4bit_use_double_quant=True,
        bnb_4bit_compute_dtype=torch.bfloat16,
        bnb_4bit_quant_type="nf4"
    )
    model = AutoModelForCausalLM.from_pretrained(
        model_name, device_map="auto", quantization_config=quant_config
    )
    tokenizer = AutoTokenizer.from_pretrained(model_name)
    tokenizer.pad_token = tokenizer.eos_token
    return model, tokenizer


Using this setup, the app dynamically generates custom datasets — in this case, I used the topic “Talking to foreigners about Ancient Egyptian monuments.”
Users can interact directly through a Gradio UI to produce educational, culturally rich datasets.

🔗 The complete workflow runs efficiently in Google Colab, using:

transformers for model loading

BitsAndBytes for memory-efficient inference

Gradio for the user interface

I’d love to hear feedback from the community — especially from those working on LLM dataset creation and educational AI tools.
