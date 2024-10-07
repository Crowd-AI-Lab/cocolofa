# CoCoLoFa:  A Dataset of News Comments with Common Logical Fallacies Written by LLM-Assisted Crowds

CoCoLoFa is a dataset introduced in the EMNLP 2024 long paper, "CoCoLoFa:  A Dataset of News Comments with Common Logical Fallacies Written by LLM-Assisted Crowds." This dataset is collected to enhance models' ability of identifying logical fallacies in online discussions. 

## Summary

CoCoLoFa contains 7,706 comments for 648 news articles, with each comment labeled for fallacy presence and type. Below image shows an example from CoCoLoFa. For each news article, we hired crowd workers to form a thread of comment. Each worker was assigned to write a comment with a specific type of logical fallacy (or a neutral argument) in response to the article. CoCoLoFa considers eight types of logical fallacy, including appeal to authority, appeal to majority, appeal to nature, appeal to tradition, appeal to worse problems, false dilemma, hasty generalization, and slippery slope.

<img src="https://github.com/user-attachments/assets/960b65fc-5d38-4c1b-b80a-18a95a11f4db" width="500">

## Statistics of CoCoLoFa

Below table shows the statistics of CoCoLoFa:

|Split|# news|# comments|w/ fallacy|w/o fallacy|
|---|:---:|:---:|:---:|:---:|
|Train|452|5370|3168|2202|
|Dev|129|1538|927|611|
|Test|67|798|481|317|
|Total|648|7706|4576|3130|

## Data Structure

Here's an example from CoCoLoFa.

```
{
    "id": 427,
    "title": "Why Did Women Journalists Strike in Spain?",
    "date": "16 March 2018",
    "author": "Maria Luz Moraleda",
    "link": "https://globalvoices.org/2018/03/16/why-did-women-journalists-strike-in-spain/",
    "content": "Some 8,000 women journalists from Spain, among them the author of this post, recently signed a manifesto called \"Journalists On Strike,\" which was read during the \"Feminist Strike\" that took place on March 8 in a dozen cities in Spain. [...]",
    "comments": [
        {
            "id": "6078",
            "news_id": 427,
            "worker_id": 18,
            "respond_to": "",
            "fallacy": "slippery slope",
            "comment": "Once you let them dictate rules against fairness, they will continue the problem. It only gets worse. Rights will be trampled and compromised."
        },
        {
            "id": "6678",
            "news_id": 427,
            "worker_id": 15,
            "respond_to": "6078",
            "fallacy": "none",
            "comment": "I understand why you think having a rule that you believe is unfair would be troubling and lead to more unfairness. I think we  need to look at the bigger picture here. A rule that you see is unfair might seem very fair to another person. Fairness is a very subjective issue and all of us will see it differently based on our experiences. Can you think of a rule or law that has been widely praised that you might see as unfair to yourself or others? Sometimes we need to look outside our own biases and see that other people can see things quite differently. Once we can see those differences we can then come together and find solutions that can meet all of our needs. I suggest that all of us meet with others with different opinions and listen to their views. That will be a great step for us all."
        }
    ]
}
```

where the fields are:
+ `id`: the ID of the news article (int)
+ `title`: the title of the news article (string)
+ `date`: the publish date of the news article (string)
+ `author`: the author of the news article (string)
+ `link`: the link to the news article (string)
+ `content`: the content of the news article (string)
+ `comments`: a list of comments written by crowdworkers (list)

For each comment, the fields are:
+ `id`: the ID of the comment (string)
+ `news_id`: the ID of the corresponding news atricle (int)
+ `worker_id`: the ID of the crowdworker (int)
+ `respond_to`: the ID of the comment that this comment responded to (string)
+ `fallacy`: the logical fallacy contained in this comment, which can be one of "appeal to authority,"  "appeal to majority,"  "appeal to nature,"  "appeal to tradition,"  "appeal to worse problems,"  "false dilemma,"  "hasty generalization,"  "slippery slope,"  or "none" (string)
+ `comment`: the comment written by a crowdworker (string)

## Citation

CoCoLoFa was created using the techniques proposed in the following paper. Please cite this work if you use CoCoLoFa.

```
@misc{yeh2024cocolofadatasetnewscomments,
      title={CoCoLoFa: A Dataset of News Comments with Common Logical Fallacies Written by LLM-Assisted Crowds}, 
      author={Min-Hsuan Yeh and Ruyuan Wan and Ting-Hao 'Kenneth' Huang},
      year={2024},
      eprint={2410.03457},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2410.03457}, 
}
```
