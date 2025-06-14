# Multimodal RAG with Videos

![image](https://github.com/user-attachments/assets/50a68ac6-5720-4dd9-bd29-ff6a12d16703)


## 🔹 Project Overview

This project demonstrates a **Multimodal Retrieval Augmented Generation (RAG)** pipeline designed to work directly with video content.
Instead of limiting retrieval to text, it integrates **both visual and linguistic components** — allowing you to search, retrieve, and generate answers from a rich pool of video data.

---

## 🔹 Why?

In a world where knowledge is increasingly represented in video format — webinars, lectures, meetings, vlogs — traditional text-centric search methods miss a large portion of information.
This pipeline lets you:

✅ Handle **videos with subtitles or without subtitles**.
✅ Combine **vision and audio modalities** alongside text.
✅ Provide contextually rich answers by retrieving segments from both the video’s dialogue and its visual content.

---

## 🔹 Applications

* Educational platforms (searchable video lectures).
* Customer service (find segments in training recordings).
* Security or surveillance (query video footage for specific events).
* Content creators (quickly retrieve scenes or quotes).

---

## 🔹 Features

* **Support for multiple scenarios:**

  * **With transcript:** parses subtitles directly.
  * **With audio only:** performs Speech-to-Text first.
  * **With no language:** relies on Visual Embedding.

* **Multimodal Embedding:**

  * Text and Audio components from subtitles or Speech-to-Text.
  * Visual components from video segments.

* **Scalable vector storage:**

  * Stores embeddings in **LanceDB**, a lightweight, scalable vector database.

* **Framework:**

  * Built on **LangChain**, **Langchain-Community**, and **OpenAI-compatible LVLMs**.

---

## 🔹 Architectural Flow

![image](https://github.com/user-attachments/assets/f48d7e56-0505-4acf-9248-28d9996aa47f)

![image](https://github.com/user-attachments/assets/b60580e3-4a81-47a0-8e58-31decbbd0654)

![image](https://github.com/user-attachments/assets/abd031a8-cc52-4706-b007-b1639b5733fe)

```text
[Video Input]
 └─ If subtitles present → extract text directly
 └─ If no subtitles → extract audio, perform Speech-to-Text
 └─ If no speech → fallback to Visual Embedding (frames)


[Preprocessing]
 └─ Split into segments (frames or subtitles)

[Embedding]
 └─ Text segments → Text Embedding Model
 └─ Visual segments → LVLM Visual Embedding Model
 └─ Audio segments → Speech Embedding Model

[Storage]
 └─ All embeddings are indexed into **LanceDB** vector store

[Query]
 └─ User's Query converts to embedding
 └─ LanceDB performs similarity search across multimodal segments

[Response]
 └─ Top-K segments retrieved
 └─ LangChain constructs context for Large Language Model (LLM)

[Final]
 └─ LLM generates a contextually rich, coherent answer
```

---

## 🔹 Tech Stack

✅ **Frameworks:**

* \[LangChain, Langchain-Community] – orchestration & retrieval
* \[LanceDB] – vector storage
* \[OpenAI-compatible LVLM] – multi-modal embedding
* \[moviepy, youtube-transcript-api, pydub] – video and audio processing
* \[Python ecosystem] – pandas, numpy, scikit-learn, etc.

✅ **Other components:**

* \[WebVTT] for subtitles
* \[ffmpeg] under moviepy for audio and video processing
* \[OpenCV] for frame extraction when no subtitles or audio available

---

## 🔹 Project Flow Summary

|         | Process                                          |
| ------- | ------------------------------------------------ |
| **1️⃣** | Extract subtitles or audio from video            |
| **2️⃣** | Split into segments (frames, text, audio)        |
| **3️⃣** | Convert segments into embeddings                 |
| **4️⃣** | Store embeddings in vector database (LanceDB)    |
| **5️⃣** | Query by transforming questions into embedding   |
| **6️⃣** | Retrieve most relevant segments                  |
| **7️⃣** | Combine context and generate answers with an LLM |

---

## 🔹 Possible Enhangements

✅ Handle multi-language subtitles
✅ Integrate automatic scene detection for more semantic segments
✅ Combine audio, text, and video signals into unified embedding
✅ Support Q\&A over large video collections
✅ Provide UI with Gradio or Streamlit for interactive search

---

## 🔹 Summary

This pipeline lets you leverage all components of a video — its audio, subtitles, and visuals — to perform semantic search and Q\&A in a way pure text or audio processing can’t match.
Using multimodal retrieval, you can uncover rich context from vast video archives quickly and accurately.





