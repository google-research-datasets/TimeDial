# TimeDial: Temporal Commonsense Reasoning in Dialog

TimeDial presents a crowdsourced English challenge set, for temporal commonsense reasoning, formulated as a multiple choice cloze task with over 1.5K carefully curated dialogs. The dataset is derived from the DailyDialog ([Li et al., 2017](https://www.aclweb.org/anthology/I17-1099/)), which is a multi-turn dialog corpus.

In order to establish strong baselines and provide information on future model development, we conducted extensive experiments with state-of-the-art LMs. While humans can easily answer these questions (97.8\%), the best T5 model variant struggles on this challenge set (73\%). Moreover, our qualitative error analyses show that the models often rely on shallow, spurious features (particularly text matching), instead of truly doing reasoning over the context. 

Detailed experiments and analyses can be found in our paper. If you use or discuss this dataset in your work, please cite it as follows:

```
@inproceedings{qin-etal-2021-timedial,
    title = "TimeDial: Temporal Commonsense Reasoning in Dialog",
    author = "Qin, Lianhui and Gupta, Aditya and Upadhyay, Shyam and He, Luheng and Choi, Yejin and Faruqui, Manaal",
    booktitle = "Proc. of ACL 2021",
    year = "2021"
}
```

## Dataset Description
TimeDial dataset consists of 1,104 dialog instances with 2 correct and 2 incorrect options with the following statistics:
|      | Avg.   |
|-----|-----|
|Turns per Dialog  | 11.7  |
|Words per Turn  | 16.5   |
|Time Spans per Dialog  | 3  |

The entire TimeDial dataset is a challenge set (`test.json`), where each example is a JSON directory with the following format:
```
{
  "id": Unique identifier,
  "conversation": Dialog context with <MASK> span,
  "correct1": Original <MASK> span,
  "correct2": Additional correct option provided by annotators,
  "incorrect1": Incorrect option #1 provided by annotators, 
  "incorrect1_rule": One of phrase matching ("Rule 1"), numeral matching ("Rule 2"), or open ended ("Rule 3"),
  "incorrect2": Incorrect option #2 provided by annotators, 
  "incorrect2_rule": One of phrase matching ("Rule 1"), numeral matching ("Rule 2"), or open ended ("Rule 3")
}
```

Here's an example from the dataset:
```json
 {
    "conversation": [
      "A:We need to take the accounts system offline to carry out the upgrade . But don't worry , it won't cause too much inconvenience . We're going to do it over the weekend .",
      "B: How long will the system be down for ?",
      "A: We'll be taking everything offline in about two hours ' time . It'll be down for a minimum of twelve hours . If everything goes according to plan , it should be up again by 6 pm on Saturday .",
      "B: That's fine . We've allowed <MASK> to be on the safe side ."
    ],
    "id": 1,
    "correct1": "forty-eight hours",
    "correct2": "50 hours ",
    "incorrect1": "two hours ",
    "incorrect1_rule": "Rule 1",
    "incorrect2": "12 days ",
    "incorrect2_rule": "Rule 2"
  }
```

**Note**: We also collected 342 extra instances for which the annotators deem there is only one unique correct answer for the context. Thus, each of those instances contains one correct option and two incorrect ones. We release those instances along with the dataset, though we did not include them in empirical study in this paper.

## Leaderboard
Stay tuned! To be updated soon.

## License
TimeDial dataset is licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).

## Contact

If you have a technical question regarding the dataset or publication, please create an issue in this repository.
