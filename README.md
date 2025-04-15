### Repository for our paper: 
# Visual-RAG: Benchmarking Text-to-Image Retrieval Augmented Generation for Visual Knowledge Intensive Queries

![header](https://github.com/visual-rag/visual-rag/blob/main/site-images/header.png?raw=true)

Arxiv https://arxiv.org/abs/2502.16636



## Annotation structure:
The annotation is a jsonl file where each row is a json object. The object sturcture is as follows:
```
{
  "images": {
    image_guid: 0/1,  # image_guid correspond to the file name in inat21 dataset. 
    ...
  },  
  "answer": list[str], # List of answers.
  "question": str,  # Question
  "sn": str, # Scientific Name
}
```

We do not redistribute the original inat21 dataset. Please collect the images according to instructions in: https://github.com/visipedia/inat_comp/tree/master/2021

Images used in Visual-RAG are under the **train** set of inat21.

<!--
**visual-rag/visual-rag** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
