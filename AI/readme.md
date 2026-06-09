# 1.0 AI, ML and Models
Applications in Day to day life:
- **Speech Recognition**
- **Computer Vision** to detect, identify, modify objects and copy text from images
- **Machine Translation** to translate one language to another
- **Chatbots**

**The Imitation Game (The Turing Test)**: If a machine can convince a human that it is also a human, then it has “passed” the Turing Test, and can be said to demonstrate intelligence.

**Artificial Intelligence** is a field of research with the goal of getting machines to perform tasks that require intelligence.

# Machine Learning: The sub field of AI
"machine learning ... is the study of algorithms that allow computer programs to automatically improve through experience."

- A **model** is a function that **takes inputs and processes those inputs to product outputs**. A model learns from experience and feedback to update how it produces these outputs, in order to perform better at a task.
- A **parameter** is a number in a model that can be updated in order to improve the model's performance at a task.
- A **neural network** is a **category of machine learning models** that consists of neurons that are grouped together in layers. Neural networks are commonly referred to as **"deep learning."**

## 1.1 Computer Vision
### 1.1.1 Object Detection
- **Object localization**: **locate** an object with a bounding box (a rectangle).
- **Image classification**: **identify the category** (a text label) that an image belongs to.
- **Object detection**: identify both the location and category of objects in an image-

### 1.1.2 Similarity Search
- **Embeddings** are lists of **numbers that describe an image** in a compact way. Embeddings can be created for images, but also other things like text, audio.The distance between two embeddings is measure of how similar the two images are.
- **Similarity search** **creates an embedding for the search image, and compares it to embeddings of other images in a database**. It identifies other images for which the embeddings are a shorter distance to the search image's embedding, and returns those associated images as "similar" to the search image This can be applied to other things like text and audio.

### 1.1.3 Image Segmentation
**Image segmentation** **identifies all the pixels that are associated with a particular object** in an image.

### 1.1.4 Optical Character Recognition
**Optical Character Recognition** **extracts text from inside an image** so that you can use the text in a word processor, email or text message.

## 1.2
### 1.2.1 Machine Translation: Words and Word Order
Homonyms and homographs: Try using context around a homonym or homograph to get the translation model to switch between the two meanings.

- Homonyms: same spelling, same pronunciation
Examples: wave, match, spring, lie, bark, bank, right, light, tire, park, can.
- Homographs: same spelling, may or may not have same pronunciation.
Examples: wind, tear, bow, contract, content, lead.

### 1.2.2 Machine Translation: Context
There is different ways like formal or informal way of addressing someone.

### 1.2.3 Machine Translation: Idiomatic vs Literal
Idioms may look different in different language.

### 1.2.4 Machine Translation: 
Distance between Two Words can change words in different languages

## 1.3 Chatbots Overview
### 1.3.1 Definition
A chatbot is a software application or computer program designed to simulate human conversation through text or voice interactions.

### 1.3.2 
Predict the next word

### 1.3.3 Hallucinations
Ask the chatbot about yourself, or ask the chatbot about a topic that it might not have much information about.Does the chatbot admit that it does not know? Or does it respond with a statement that is not correct?

### 1.3.4 Memory
Start a new chat (to clear the memory) when you do not want your chat history to affect the results of your current prompt.

### 1.3.5 Level of Difficulty
refers to the difficulty of producing the output of a prompt
Proprietary chatbots that you can access through a website:
https://chatgpt.com/
https://gemini.google.com/app
https://claude.ai/chats
https://copilot.microsoft.com/
https://chat.mistral.ai/chat

Open models that you can access through a website:
https://www.meta.ai/
https://coral.cohere.com/

Downloadable, compressed models
https://lmstudio.ai/

### 1.3.6 Use Multiple Chatbots
to make sure the data is correct. Use Open Source models.


### 1.3.7 How to write your prompts
- Write more than you’re used to.
- Break into sub-tasks
- Set expectations (“if you’re not sure, say so”)
- Output format (table, list, bullet points)
- Add structure in the prompt (sub-headers, numbered lists, delimiters)
- Give the chatbot a persona (a role, style of communication)
- Give examples (few shot prompting)
- Ask a chatbot to review its work (reflect on its previous output)

## 1.5 Generative AI and Other Vocabulary Words
- Generative AI outputs are new, and can be used as inputs to other models, for other tasks, or for model training.
- **Pre-training** teaches the model general knowledge.
- **Instruction tuning** teaches the model how to follow instructions.
- **Foundation models** can perform many tasks.
- **Transformers** are the technology that makes modern language models possible.
- **Non-generative AI** focuses on selecting the correct answer from predefined possibilities.
GPT stands for Generative Pre-trained Transformer.

Three **kinds of model compression** are **quantization, distillation, and pruning**.

- **Quantization** stores parameters in fewer bits, from 32 bits to 16 or 8 bits.
- **Distillation** trains a smaller model using the outputs from the larger, original model.
- **Pruning** identifies less important parameters in a model and sets them to zero, to save space.

A GPU, a G**raphics Processing Unit, is hardware that can perform math operations in parallel.** A **CPU can delegate tasks** such as model training or inference to a GPU to perform the task more efficiently.

**Retrieval Augmented Generation (RAG)**: uses a vector database to store domain specific information, which helps a **large language model answer domain specific questions.**

**Fine-tuning** a model on domain specific information allows it to answer questions or **perform tasks with this domain specific information.**

**Agents** are large language models that are wrapped in additional code that allows them to **make decisions and take actions independently.**

**Skill stacking** is the idea that you can stand out by being pretty **good at two or more unique sets of skills**, as an alternative to being really, really good at one set of skills.









