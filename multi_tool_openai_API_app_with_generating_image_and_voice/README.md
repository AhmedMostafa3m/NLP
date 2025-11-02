![tape image](https://github.com/AhmedMostafa3m/NLP/blob/b0a13b8549fc256b5d9dd669393d9e821950a993/multi_tool_openai_API_app_with_generating_image_and_voice/Screenshot%202025-11-01%20155433.png)

# 🤖 AI Assistant that Chats and Generates Audio and Images

An interactive AI-powered assistant built in a single Jupyter Notebook that can **chat**, **speak using text-to-speech**, and **generate images** dynamically.  
This project integrates OpenAI’s GPT models with Gradio to provide a full multimodal experience — users can send messages, hear AI responses, and view generated visuals, all in one app.

---

## 🚀 Features

- 💬 **Conversational Chat** – Interact naturally with an AI assistant powered by OpenAI GPT models.  
- 🔊 **Text-to-Speech (TTS)** – Converts AI responses into realistic human-like voice using `gpt-4o-mini-tts`.  
- 🖼️ **Image Generation** – Produces creative or context-related images from text prompts.  
- 🧠 **Tool Use Integration** – Demonstrates OpenAI tool calls and structured data handling (JSON-based).  
- 🖥️ **Gradio Interface** – Clean, user-friendly interface for real-time interaction.  
- ⚙️ **Fully Contained Notebook** – All logic, dependencies, and app code are inside one notebook file.

---

## 🧩 Project Structure

The notebook (`week2 EXERCISE.ipynb`) contains all steps required to understand and run the application.  
Here’s a high-level breakdown of its sections:

2️⃣ Database & Helper Functions

Uses SQLite for simple data storage (e.g., ticket prices, booking codes).

Defines helper functions like:

get_ticket_price(city) – retrieves ticket price from the database.

book_flight(city) – simulates booking logic and generates booking codes.

3️⃣ AI Integration

Implements OpenAI Chat API to process user inputs.

Demonstrates structured tool calls using tool_call.function.arguments and json.loads(...).

4️⃣ Audio & Speech Handling

Defines talker(message) function using:

response = openai.audio.speech.create(
    model="gpt-4o-mini-tts",
    voice="onyx",
    input=message
)


Returns an MP3/WAV audio output playable through Gradio.

5️⃣ Image Generation Logic

Ensures image outputs are valid PIL.Image or numpy array objects (compatible with gr.Image).

6️⃣ Chat Loop & Response Handling

Implements a structured response system:

responses.append({
    "role": "tool",
    "content": json.dumps({input_name: indata, output_name: outdata}),
    "tool_call_id": tool_call.id
})


Ensures consistent state management between tools and chat.

7️⃣ Gradio Interface

Combines all components:

Textbox for text input.

Microphone input for speech (optional).

Audio output to play TTS results.

Image output to display generated images.

Launches a real-time web UI.

🧠 Technical Highlights

Tool Call Parsing:
The app decodes structured responses from GPT functions using:

arguments = json.loads(tool_call.function.arguments)


Regular Expressions & Validation:
Uses re.match(...) != None to ensure correct code patterns.

Dynamic JSON Handling:
Demonstrates both JSON serialization and deserialization for AI communication.

🧰 Installation

This project uses uv
 as the environment manager for reproducibility and speed.

1️⃣ Install uv
pip install uv

2️⃣ Sync Environment

In your project directory:

uv sync


This will install all required dependencies automatically.

▶️ Running the Application

Once inside the uv environment, launch the notebook and run all cells:

uv run jupyter notebook


Open the file:

week2 EXERCISE.ipynb


Then execute all cells to start the Gradio app.
After startup, you’ll see a local Gradio link (e.g. http://127.0.0.1:7860) — open it in your browser to start chatting with your AI assistant!

📸 Example Usage
Action	Description
🗣️ Speak	Type or talk to your assistant using the microphone.
🧏 Listen	Hear back the AI’s spoken response.
🖼️ Generate	Ask the AI to “draw a sunset over Tokyo” — and get an image instantly.
⚠️ Troubleshooting

Response content shorter than Content-Length
→ Happens if Gradio or Uvicorn prematurely closes a connection. Try restarting the notebook.

Audio or Image not displaying?
→ Make sure you return either a valid file path, URL, or PIL.Image object in your response functions.

📂 Repository Contents
📦 AI-assistant-that-chats-and-generates-audio-and-images
 ┣ 📜 week2 EXERCISE.ipynb
 ┣ 📜 README.md
 ┣ 📜 requirements.txt  (optional)
 ┗ 📜 .gitignore

🧑‍💻 Author

Ahmed Mostafa
AI Engineer | Machine Learning & Computer Vision Enthusiast
🚀 Building intelligent assistants that see, speak, and understand.

🪪 License

This project is licensed under the MIT License — you are free to use, modify, and distribute it with attribution.

🌟 Acknowledgments

OpenAI
 for GPT and TTS models.

Gradio
 for the easy-to-use web interface.

uv
 for efficient Python environment management.


