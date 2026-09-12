# Local AI Model Manager

A Python-based utility for **discovering, downloading, configuring, and running AI models locally** using [Ollama](https://ollama.com/) and [Open WebUI](https://github.com/open-webui/open-webui).

The program is designed to make local AI setup as simple as possible. It detects the host computer's hardware specifications, evaluates whether available AI models are suitable for the system, performs the required setup automatically, and configures Open WebUI for an easy browser-based chat experience.

---

## ✨ Features

* 🔍 **Discover AI models from the Internet**
* 📋 **Display available models that can be downloaded**
* ➕ **Add custom/new models**
* 💻 **Automatically detect host PC specifications**
* ⭐ **Show `Recommended` status based on available hardware**
* 📥 **Download AI models automatically**
* 🦙 **Configure and use Ollama**
* 🌐 **Configure Open WebUI**
* ⚙️ **Automatically perform required setup/configuration**
* ⏭️ **Skip already completed setup steps**
* 🔄 **Avoid unnecessarily downloading/installing existing components**
* 🚀 **Launch the local AI Web UI**
* 🖥️ **Create an Open WebUI shortcut**
* 📊 **Help users select models according to their PC capabilities**
* 🧩 **Support adding models beyond the predefined list**

---

# 🧠 How It Works

The program follows a simple workflow:

```text
                  ┌─────────────────────┐
                  │     Start Program   │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Detect Host Hardware│
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Search Model Sources│
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Display Model List  │
                  │ + Recommended Tag   │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Select / Add Model  │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Download / Configure│
                  │       Ollama        │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Configure Open WebUI│
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Create WebUI        │
                  │ Shortcut            │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │    Run Local AI     │
                  └─────────────────────┘
```

---

# 🖥️ Hardware Detection

Before recommending models, the application reads the host PC's available hardware information.

Depending on the operating system and available system information, this can include:

* CPU
* CPU cores / threads
* System RAM
* GPU
* GPU VRAM
* Operating system
* Architecture
* Available storage
* Other relevant hardware information

The detected specifications are used to determine whether a model is suitable for the computer.

Example:

```text
========================================
        HOST PC SPECIFICATIONS
========================================

CPU       : Intel Core i5
RAM       : 16 GB
GPU       : NVIDIA RTX 4050
VRAM      : 6 GB
OS        : Windows
Architecture : x64

========================================
```

---

# ⭐ Recommended Model Detection

Each model can be evaluated against the detected hardware.

Models that are considered suitable for the current system are marked:

```text
[✓] Recommended
```

Models that may require additional resources can be displayed differently, for example:

```text
[!] High Resource
```

or:

```text
[ ] Not Recommended
```

The recommendation system is intended to help users avoid downloading models that are impractical for their hardware.

> **Note:** `Recommended` is a hardware-based guidance indicator, not a guarantee of a particular inference speed or performance level.

---

# 📦 Model Management

The application provides a model management interface where users can browse available models.

A typical model list can look like:

```text
========================================================
                 AVAILABLE AI MODELS
========================================================

  #   MODEL              SIZE       STATUS
--------------------------------------------------------
  1   Model-A            4 GB       ✓ Recommended
  2   Model-B            8 GB       ✓ Recommended
  3   Model-C           14 GB       ! High Resource
  4   Model-D           32 GB       ✗ Not Recommended
--------------------------------------------------------

  A   Add New Model
  R   Refresh Models
  Q   Quit
========================================================
```

Select a model to begin the download and setup process.

---

# ➕ Adding a New Model

The program is not limited to the models included in its default model list.

Users can add a new model by providing the required model information or Ollama-compatible model reference.

Example workflow:

```text
Select an option:

1. Download Existing Model
2. Add New Model
3. Refresh Model List
4. System Information
5. Open WebUI
6. Exit

> 2
```

The application then collects the required information and evaluates the model against the detected system hardware where possible.

---

# 🦙 Ollama

The project uses **Ollama** as the local model runtime.

Ollama provides the backend responsible for running the downloaded AI models locally.

The program can check whether the required Ollama installation/configuration is already present.

If it is already configured:

```text
[✓] Ollama detected
[✓] Ollama configuration found
[→] Skipping installation...
```

If it is missing:

```text
[!] Ollama not found
[→] Starting Ollama setup...
```

This prevents the program from unnecessarily repeating setup steps.

---

# 🌐 Open WebUI

After Ollama is configured, the program configures **Open WebUI** as the graphical interface for interacting with the local models.

Open WebUI provides a browser-based interface where users can:

* Chat with local AI models
* Select installed models
* Manage conversations
* Interact with the Ollama backend
* Use a familiar ChatGPT-style interface

The goal of this project is to automate the configuration so the user does not have to manually configure every component.

---

# 🚀 Automatic Setup

The setup process is designed to be **idempotent**.

In other words, the program checks whether a required component already exists before performing an installation or configuration step.

For example:

```text
Checking environment...

[✓] Python environment detected
[✓] Ollama detected
[✓] Required configuration found
[✓] Open WebUI detected
[→] Skipping completed steps

Starting remaining configuration...
```

This makes it possible to run the program again without unnecessarily repeating previously completed operations.

---

# 🔗 Open WebUI Shortcut

Once Open WebUI has been configured, the program creates a shortcut for convenient access.

The shortcut allows the user to launch/open the local WebUI without manually remembering the local address or starting the interface every time.

The exact shortcut behavior can depend on the operating system and configuration.

---

# 📋 Requirements

## Minimum

The exact requirements depend on the AI model being used.

Generally, you should have:

* Python 3.x
* 64-bit operating system
* Sufficient system RAM
* Sufficient disk space
* Ollama-compatible environment
* Internet connection for initial model/software downloads

For GPU acceleration, the appropriate GPU drivers and runtime support should also be installed.

---

# 💾 Storage Requirements

AI models can be large.

Before downloading a model, make sure sufficient disk space is available.

Approximate model sizes vary significantly depending on:

* Model architecture
* Parameter count
* Quantization
* Model format
* Runtime requirements

For example:

```text
Small models       → Lower storage / RAM requirements
Medium models      → Moderate requirements
Large models       → High RAM / VRAM requirements
Very large models  → High-end hardware recommended
```

The application should therefore be used together with the hardware recommendation indicator rather than selecting models based solely on download size.

---

# ⚡ GPU Acceleration

If a compatible GPU is available, Ollama may be able to use it for accelerated inference.

The actual performance depends on:

* GPU model
* VRAM
* CPU
* System RAM
* Model architecture
* Quantization
* Context size
* Number of layers offloaded to GPU
* Other running applications

A model marked `Recommended` should therefore be understood as **a compatibility/resource recommendation**, not a performance benchmark.

---

# 🛠️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

Enter the project directory:

```bash
cd YOUR_REPOSITORY
```

Install the Python dependencies:

```bash
pip install -r requirements.txt
```

Run the program:

```bash
python main.py
```

> Replace `main.py` with the project's actual entry-point filename if it differs.

---

# ▶️ Usage

Start the application:

```bash
python main.py
```

The program will then:

1. Detect the host PC specifications.
2. Check the existing environment.
3. Detect required software/configuration.
4. Search/load available AI models.
5. Evaluate models against the detected hardware.
6. Display the model list.
7. Mark suitable models as `Recommended`.
8. Allow the user to select a model.
9. Download/configure the selected model.
10. Configure Ollama.
11. Configure Open WebUI.
12. Create the Open WebUI shortcut.
13. Launch the local AI environment.

---

# 🔄 Re-running the Program

You can run the program again after the initial setup.

The application checks the existing environment before performing setup tasks.

For example:

```text
Checking Ollama...
[✓] Already installed

Checking model...
[✓] Already available

Checking Open WebUI...
[✓] Already configured

Checking shortcut...
[✓] Already exists

Nothing unnecessary to install.
```

This allows the program to function as both an **initial setup wizard** and a **local AI model manager**.

---

# 🧩 Project Structure

A typical project structure may look like:

```text
local-ai-model-manager/
│
├── main.py
├── requirements.txt
├── README.md
│
├── models/
│   └── ...
│
├── config/
│   └── ...
│
├── utils/
│   └── ...
│
└── scripts/
    └── ...
```

The actual structure may differ depending on the implementation.

---

# 🔐 Security Considerations

Because the application can discover and download software/models from the Internet, users should take care when adding custom model sources.

Only use model sources that you trust.

Before downloading a custom model, verify:

* The source is legitimate.
* The model is compatible with Ollama.
* The download URL is correct.
* The model has sufficient documentation.
* The model does not contain unexpected executable content.

The program should not be considered a security scanner for third-party model repositories.

---

# 🌍 Internet Access

An Internet connection is generally required for:

* Discovering models
* Downloading models
* Installing required software
* Installing Python dependencies
* Initial Open WebUI setup

Once everything is installed, the local model inference itself can operate without an Internet connection, provided the selected model and required software are already available locally.

---

# 🧠 Local AI

One of the primary goals of this project is to make local AI accessible without requiring users to manually perform multiple technical setup steps.

Instead of:

```text
Find model
   ↓
Check hardware
   ↓
Install runtime
   ↓
Download model
   ↓
Configure runtime
   ↓
Install/configure WebUI
   ↓
Configure connection
   ↓
Create shortcut
   ↓
Start AI
```

the project aims to provide:

```text
        RUN PROGRAM
             ↓
       SELECT MODEL
             ↓
      AUTOMATIC SETUP
             ↓
       START WEB UI
             ↓
          CHAT
```

---

# 🏗️ Design Goals

The project is built around several principles:

### 1. Simple

Users should not need extensive command-line knowledge to run local AI.

### 2. Automatic

Common installation and configuration tasks should be automated.

### 3. Hardware-aware

The application should consider the user's available hardware when recommending models.

### 4. Repeatable

Running the program multiple times should not unnecessarily repeat completed setup operations.

### 5. Extensible

Users should be able to add new models instead of being restricted to a fixed model list.

### 6. Local-first

Once the required software and models are downloaded, inference can be performed locally.

---

# ⚠️ Important Notes

### Model compatibility

Not every AI model available on the Internet is directly compatible with Ollama.

A model may require:

* Conversion
* Quantization
* A compatible model format
* A custom Modelfile
* Additional configuration

The application should therefore verify model compatibility before attempting installation whenever possible.

### Hardware recommendations

Hardware requirements are not determined solely by parameter count.

Actual requirements can vary according to:

* Quantization
* Context length
* Architecture
* GPU offloading
* Runtime configuration
* Number of concurrent users

Therefore, the `Recommended` indicator should be treated as guidance rather than an absolute guarantee.

---

# 🐛 Troubleshooting

## Ollama is not detected

Make sure Ollama is installed and running correctly.

Check that the Ollama executable is available to the system and that its local service is accessible.

---

## Model download fails

Possible causes include:

* Internet connection problems
* Invalid model reference
* Model repository unavailable
* Insufficient disk space
* Incorrect model configuration

Try refreshing the model information and checking the model source.

---

## Model is marked Not Recommended

This generally indicates that the detected hardware may not provide sufficient resources for comfortable operation of the model.

Consider using:

* A smaller model
* A more heavily quantized model
* A model with fewer parameters

---

## Open WebUI does not open

Check that:

1. Ollama is running.
2. Open WebUI is running.
3. The configured WebUI address is correct.
4. Required ports are available.
5. The local firewall is not blocking the service.

---

# 🤝 Contributing

Contributions are welcome.

Possible areas for improvement include:

* Additional model sources
* Better hardware detection
* Improved model recommendation algorithms
* More operating-system support
* Better download error handling
* Model benchmarking
* Automatic GPU detection
* More detailed resource estimation
* Improved UI/CLI experience
* Additional WebUI integrations

To contribute:

```bash
git fork
git clone <your-fork>
git checkout -b feature/my-feature
```

Make your changes, test them, and submit a pull request.

---

# 📜 License

Add the project's license here.

For example:

```text
MIT License
```

If this project uses a different license, replace the above accordingly.

---

# 🙏 Acknowledgements

This project builds upon the local AI ecosystem provided by:

* **Ollama** — local AI model runtime
* **Open WebUI** — web-based interface for local AI
* The developers and communities behind the open-source AI models supported by the project

---

# ⭐ Project Goal

The ultimate goal of this project is to turn local AI deployment from a complicated multi-step process into a simple workflow:

```text
┌──────────────────────────────┐
│      LOCAL AI MANAGER        │
├──────────────────────────────┤
│                              │
│  🖥 Detect PC Hardware       │
│                              │
│  🔍 Find AI Models           │
│                              │
│  ⭐ Recommend Models         │
│                              │
│  📥 Download Models          │
│                              │
│  🦙 Configure Ollama         │
│                              │
│  🌐 Configure Open WebUI     │
│                              │
│  🔗 Create Shortcut          │
│                              │
│  🚀 Start Local AI           │
│                              │
└──────────────────────────────┘
```

**Choose a model → Let the program handle the setup → Start chatting locally.**

---

## 📌 Disclaimer

This project is intended to simplify local AI setup and model management. Model availability, hardware compatibility, third-party repositories, Ollama behavior, and Open WebUI functionality may change over time.

Always verify third-party downloads and ensure that your system has adequate hardware resources before installing large AI models.
