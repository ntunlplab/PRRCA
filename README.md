# Peer Review and Rebuttal Counter-Arguments (PRRCA) dataset
Dataset for the paper **Incorporating Peer Reviews and Rebuttal Counter-Arguments for Meta-Review Generation**.

## Content
- [Folder Structure](#Folder-Structure)
- [ICLR_Submission](#ICLR_Submission)
    - [Dataset Structure](#Dataset-Structure)
    - [Instance](#Instance)
- [MetaReview_Generation_Corpus](#MetaReview_Generation_Corpus)
    - [Corpus Instance](#Corpus-Instance)
    - [Dataset Analytic](#Dataset-Analytic)
    - [Cited Corpus](#Cited-Corpus)

## Folder Structure
```
├── ICLR_Submission (separated by years)
│     ├── ICLR_2017.json
│     ├── ICLR_2018.json
│     ├── ICLR_2019.json
│     ├── ICLR_2020.json
│     ├── ICLR_2021.json
│     └── ICLR_2022.json
│
├── MetaReview_Generation_Corpus (access by each submission year and forum id)
│     ├──  2020_H1gBhkBFDH.json
│     ├──  2019_rket4i0qtX.json
│     ├──           ...
│     ├──           ...
│     ├──           ...
│     └── 2021_ASAJvUPWaDI.json 
```

Do not upload ICLR_Submission since it exceeds the maximum file size limit. Can download it via the [google drive link](https://drive.google.com/drive/folders/1AJPxDATB-PW9mBWl__4DTrbRluTygpr_?usp=sharing)

---
## ICLR_Submission
> This folder contains all the submission related data we crawl from OpenReview platform.

> The raw data is available as `json` files separated by its submission year.

> Each submission can be accessed by its forum id

### Dataset Structure
![ICLR_Submission Dataset Structure](https://i.imgur.com/PvE2rGm.png)

### Instance

```
example of item access by the json dictionary

├── forum (Sy0GnUxCb - Unique id from Openreview)
│
├── submission_title (paper title)
│
├── reviews (subdict access with review id)
│    │ 
│    ├──(key) Sy0GnUxCb - 0
│    │    ├── review_id (Sy0GnUxCb - 0)
│    │    ├── review_title
│    │    ├── review (review content)
│    │    ├── rating (review score from 0 to 9)
│    │    │
│    │    ├── first_reply (rebuttal content)
│    │    │     ├── title
│    │    │     ├── tcdate (create time)
│    │    │     ├── tmdate (last modified time)
│    │    │     ├── number (thread order sorted by tcdate)
│    │    │     ├── id (thread id)
│    │    │     ├── replyto (reply content id)
│    │    │     ├── writer
│    │    │     ├── content
│    │    │     └── aspect_labels
│    │    │
│    │    ├── tcdate (review create time)
│    │    ├── tmdate (review last modified time)
│    │    │
│    │    ├── discussion_thread (list of discussion of the reviews)
│    │    │      └──list of discussion that same as first_reply structure
│    │    │
│    │    ├── conformity (review quality) (list of conformity score range from 1 to 4)
│    │    │     ├── WorkerId
│    │    │     └── rating (1 to 4)
│    │    │
│    │    ├── aspect_labels (list of aspect polarity)
│    │    │     ├── start position (character index)
│    │    │     ├── end position (character index)
│    │    │     └── polarity (motivation_positive)
│    │    │
│    │    ├── has_RR_pair (True, False) (Whether have RR alignment pair)
│    │    │
│    │    ├── Review_ADU (List of Review's ADUs with label)
│    │    │     ├── start (start index of ADU)
│    │    │     ├── end (end index of ADU)
│    │    │     ├── label (ADU label align with Reply label)
│    │    │     └── sent (ADU span)
│    │    │
│    │    └── Reply_ADU (List of Reply's ADUs with label similar to Review_ADU)
│    ├──
│    
├── Decision (one of four)
│     ├──Accept (Poster)
│     ├──Accept (Spotlight)
│     ├──Accept (Oral)
│     └──Reject
│    
└── MetaReview
```

---
## MetaReview_Generation_Corpus

> The data we used to generated MetaReview

> For each submission, we collect the review, rebuttal content, reviewers ratings, and the final decision.

> The raw data is available as `json` files separated ***by each submission*** with its *++submission year and forum id++*.

### Corpus Instance
<div itemscope itemtype="http://schema.org/Dataset">
<table>
  <tr>
    <th>key</th>
    <th>value</th>
  </tr>
  <tr>
    <td>year</td>
    <td><code itemprop="year">2020 (Submission year)</code></td>
  </tr>
  <tr>
    <td>forum</td>
    <td><code itemprop="forum">HkxlcnVFwB (Unique id from Openreview)</code></td>
  </tr>
  <tr>
    <td>title</td>
    <td><code itemprop="title">GenDICE: Generalized Offline Estimation of Stationary Values (Submission Paper Title)</code></td>
  </tr>
  <tr>
    <td>decision</td>
    <td><code itemprop="decision">Accept (Oral)</code></td>
  </tr>
  <tr>
    <td>meta_review</td>
    <td><code itemprop="meta_review">The authors develop a framework for off-policy value estimation for infinite horizon RL tasks, for estimating the stationary distribution of a Markov chain. Reviewers were uniformly impressed by the work, and satisfied by the author response. Congratulations! </code></td>
  </tr>
  <tr>
    <td>reviews</td>
    <td>
      <div itemscope itemtype="http://schema.org/Organization" itemprop="provider">
        <table>
          <tr>
            <th>key</th>
            <th>value</th>
          </tr>
          <tr>
            <td>review_id</td>
            <td><code itemprop="review_id">HkxlcnVFwB-0 (Review index)</code></td>
          </tr>
          <tr>
            <td>review_text</td>
            <td><code itemprop="review_text">This paper proposes a new estimator to infer the stationary distribution of a Markov chain, with data from another Markov chain. This paper tackles an interesting problem with an increasing number of studies in the reinforcement learning community and gives a practical algorithm with strong empirical justification, as well as theoretical justification. I think this paper should be accepted.
</code></td>
          </tr>
          <tr>
            <td>reply_text</td>
            <td><code itemprop="reply_text">Thanks for the encouraging comments.  We will keep improving the draft. We have refined the paper as listed above in the summary of revisions.Best,Authors.
</code></td>
          </tr>
          <tr>
            <td>rating</td>
            <td><code itemprop="rating">8: Accept</code></td>
          </tr>
        </table>
      </div>
    </td>
  </tr>
</table>
</div>

### Dataset Analytic
| Year | # Submissions| Avg Rating | Acceptance | Avg Meta-review Len|
| ---- | :----------: | :--------: | :--------: | :--------: |
|2017  |     293      |    5.94    |   45.39%   |114.83|
|2018  |     677      |    5.70    |   43.72%   | 104.56|
|2019  |     1153     |    5.69    |   41.63%   | 147.11|
|2020  |     1807     |    4.68    |   34.86%   | 128.92|
|2021  |     2208     |    5.62    |   35.73%   | 182.96|
|**Total**|**6138** |    5.40    |   37.93%   |148.42|

### Other Cited Corpus
* Aspect Typology Label 
    * Paper - [Can We Automate Scientific Reviewing?](https://arxiv.org/pdf/2102.00176.pdf)
    * Link - [Dataset (Aspect Tagger)](https://github.com/neulab/ReviewAdvisor)
* Argumentative Structure
    * Paper - [APE: Argument Pair Extraction from Peer Review and Rebuttal
via Multi-task Learning](https://aclanthology.org/2020.emnlp-main.569.pdf)
    * Link - [Review Rebuttal Dataset](https://github.com/LiyingCheng95/ArgumentPairExtraction)
