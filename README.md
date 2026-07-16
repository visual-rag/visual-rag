### Repository for our paper: 
# Visual-RAG: Benchmarking Text-to-Image Retrieval Augmented Generation for Visual Knowledge Intensive Queries



![header](https://github.com/visual-rag/visual-rag/blob/main/site-images/header.png?raw=true)

**Update: Visual-RAG will be presented at SIGIR 2026!**


If you find our work useful, please cite with the following bibtex:

```
@inproceedings{
  visualrag,
  title={Visual-RAG: Benchmarking Text-to-Image Retrieval Augmented Generation for Visual Knowledge Intensive Queries},
  author={Yin Wu and Quanyu Long and Jing Li and Jianfei Yu and Wenya Wang},
  booktitle={Proceedings of the 49th International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR '26)},
  year={2026},
  doi={10.1145/3805712.3808615}
}
```

Arxiv https://arxiv.org/abs/2502.16636
(Arxiv version is not completely identical with SIGIR version; as we are presenting in SIGIR Resource Track (6 pages, without Appendix), the arxiv version contains more details; v3 of the arxiv manuscript to be updated soon)


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
