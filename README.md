# LUMS Course Assistant 🎓

_A Retrieval-Augmented Generation (RAG) model for academic course selection assistance at LUMS_

![Project Banner](assets\RAG_Poster.png)

## 📌 Project Overview

The LUMS Course Assistant is an advanced AI system designed to help students at Lahore University of Management Sciences (LUMS) make informed course selection decisions. By leveraging Retrieval-Augmented Generation (RAG) architecture, the system provides personalized recommendations based on historical course reviews and official course outlines.

## ✨ Key Features

- **Course Recommendations**: Get personalized suggestions based on your academic level and interests
- **Detailed Reviews**: Access comprehensive student reviews about difficulty, workload, and teaching quality
- **Semester Planning**: Discover which courses are typically offered in specific semesters
- **Conversational Interface**: Natural language interaction with our AI assistant
- **Course Outlines**: Official component breakdowns, prerequisites, and study resources
- **Context-Aware Responses**: Maintains conversation context for follow-up questions

## 🛠️ Technical Implementation

### Data Collection

- 471 student reviews from Google Forms and LUMS Discussion Forum
- 170 course outlines from LUMS Registrar Portal
- Manually annotated metadata (course abbreviations, aliases, offering semesters)

### Technology Stack

| Component            | Technology Used                     | Key Benefits                       |
| -------------------- | ----------------------------------- | ---------------------------------- |
| Embeddings           | OllamaEmbeddings (nomic-embed-text) | State-of-the-art retrieval         |
| Vector Database      | Chroma DB                           | Open source, high performance      |
| Large Language Model | Mistral-7B-Instruct-v0.2            | 7B parameters, instruct fine-tuned |
| Framework            | LangChain                           | Modular design, RAG optimized      |
| Interface            | Gradio + ngrok                      | User-friendly, web accessible      |

### System Architecture

1. **Document Loading**:
   - `Docx2txtLoader` for text documents
   - `PyPDFLoader` for course outlines
2. **Vector Storage**: Chroma DB with nomic-embed-text embeddings
3. **Retrieval**: Similarity-based document retrieval
4. **Generation**: Mistral-7B-Instruct with custom prompt engineering
5. **Memory**: `ConversationBufferMemory` (K=3 interactions)

## 💡 Successful Use Cases

Here are real examples of our system in action:

### Case 1: Instructor Inquiry

![Inquiry one](assets\use_case_introtoAI.png)

### Case 2: Course Recommendation

![inquiry two](assets\Use_case_econ_meco.png)

## 👥 Development Team

| Name               | ID       | Key Contributions                                            |
| ------------------ | -------- | ------------------------------------------------------------ |
| Mustafa Abbas      | 25100079 | Project documentation, LLM research, Pipeline Architecture   |
| Raahem Nabeel      | 25100079 | Pipeline architecture, debugging                             |
| Ibrahim Farrukh    | 25100227 | Data collection lead, course outlines, Pipeline Architecture |
| Jawad Saeed        | 25100094 | Vector embeddings, LLM experimentation                       |
| Safiullah Sarfaraz | 25100227 | Data collection, EDA, annotation, Pipeline Architecture      |

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Ollama (for embeddings)
- HuggingFace API key

### Installation

```bash
git clone https://github.com/yourusername/lums-course-assistant.git
cd lums-course-assistant
pip install -r requirements.txt
```
