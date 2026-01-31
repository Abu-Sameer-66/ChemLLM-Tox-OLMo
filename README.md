
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&ColorList=896A15,6E8915,98351F&height=280&section=header&text=ChemLLM%20Adapter&fontSize=50&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Generative%20AI%20for%20Molecular%20Toxicity&descAlignY=60&descAlign=50" width="100%"/>

  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=0F9D58&center=true&vCenter=true&width=700&lines=Loading+OLMo-7B+Base+Model...;Injecting+LoRA+Adapters+(r%3D32)...;Processing+Tox21+SMILES+Structures...;Bio-Chemical+Neural+Link+ESTABLISHED." />
  </a>

  <br/>
  
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" />
  <img src="https://img.shields.io/badge/DeepChem-Bio_AI-00C853?style=for-the-badge&logo=moleculer&logoColor=white" />
  <img src="https://img.shields.io/badge/LLM-OLMo_7B-000000?style=for-the-badge&logo=openai&logoColor=white" />

</div>

---

## 🧬 Project Mission
> **"Teaching Language Models to 'Read' Chemistry."**

**ChemLLM-Adapter** is a state-of-the-art Fine-Tuning Engine designed to bridge the gap between **Generative AI** and **Computational Toxicology**. 
By leveraging **QLoRA (Quantized Low-Rank Adaptation)**, this system adapts the massive **OLMo-7B** model to predict molecular toxicity directly from chemical sequences (SMILES), democratizing drug discovery research on consumer hardware.

---

## 🔬 Core Engineering Innovations

| Feature | The Tech Behind It |
| :--- | :--- |
| **🧠 QLoRA Fine-Tuning** | Implements **4-bit Normal Float (nf4)** quantization to compress the 7B model, while attaching trainable **LoRA adapters** (`r=32`, `alpha=64`) for efficient learning. |
| **🧪 Molecular Tokenization** | Converts raw chemical formulas (e.g., `C(=O)O`) into structured semantic prompts: <br> `Molecule: [SMILES] \nTask: [Assay] \nIs Toxic: ?` |
| **⚖️ Smart Balancing** | The `dataset.py` engine automatically handles the severe class imbalance in Tox21 by applying **3x Oversampling** to rare toxic samples. |
| **🛡️ DeepChem Integration** | Uses **RDKit** and **DeepChem** loaders to validate molecular integrity before ingestion into the neural network. |

---

## ⚙️ System Architecture
*Visualizing the Data Flow from Molecule to Prediction:*

```mermaid
graph TD
    A[🧪 Tox21 Raw Data] -->|Validation| B(dataset.py)
    B -->|Tokenize| C{Molecules}
    D[🤖 OLMo-7B Model] -->|Quantize| E(model.py)
    C & E -->|Train Loop| F[train.py]
    F --> G[🚀 Fine-Tuned Adapter]
