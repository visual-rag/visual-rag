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

---

## Update: v2 annotations

We discovered errors in the v1 annotation files (that some rows contain "HOLD" as question but no meaningful actual question), due to version control issue.
We have gone through another round of check and verification of the annotations, and uploaded the v2_anno.jsonl file.

There is a new key in the v2 json object, "is_changed_v2", to denote how it is changed from v1. It has three possible values: "unchanged"; "updated_image_label" - the question-answer pair is not changed, but image labels are changed which will affect retrieval scores; "updated_qa" - the question-answer pair is changed, and image labels are also updated correspondingly.

There are 278 rows unchanged, 61 rows updated_image_label, 35 rows updated_qa, total 374 rows remaining. (All v1 questions with "HOLD" are removed)

We are really sorry for additional effort caused if you have already in-progress training or inference works with the erroneous v1 annotations.

---

## Partial results with v2 annotations

We have evaluated the v2 dataset with Qwen2.5-VL-7B-Instruct, Phi-4-multimodal-instruct, InternVL3-8B, and GPT-4o

|                     | Phi4  | Qwen2.5VL | InternVL3 | GPT4o |
|---------------------|-------|-----------|-----------|-------|
| Zeroshot (No Image) | 31.68 | 34.84     | 25.67     | 49.33 |
| One Random GT Image | 36.71 | 36.66     | 35.94     | *54.67* |
|                     |       |           |           |       |
| Retrieved topk=1    | 33.16 | 37.96     | 31.55     | 22.65 |
| k=3                 | **34.22** | 39.44     | 37.3      | 38.5  |
| k=5                 | 32.49 | 39.84     | 36.9      | 43.45 |
| k=7                 | 32.49 | 38.99     | **38.24**     | 46.52 |
| k=10                | 33.56 | 42.91     | 37.03     | 46.93 |
| k=15                | **34.22** | 42.78     | 35.16     | 47.33 |
| k=20                | 34.09 | **43.44**     | 37.97     | **50**    |
|                     |       |           |           |       |
| 1-in-k, k=3         | **35.59** | 41.38     | 36.90     | 45.58 |
| k=5                 | 34.25 | **43.29**     | 34.12     | 49.13 |
| k=7                 | 33.34 | 42.69     | **35.27**     | 50.92 |
| k=10                | 33.34 | 41.37     | 33.48     | 51.74 |
| k=15                | 32.77 | 43.10     | 34.20     | **52.21** |
| k=20                | 33.36 | 42.06     | 34.71     | 51.72 |

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
