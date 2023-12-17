# CSIE 5043 Machine Learning Final Project
\[2023/12/02 Update\] new station: `500109089`

\[2023/11/26 Update\] new station: `500107143`

\[2023/11/11 Update\] new station: `500110084`

\[2023/11/08 Update\] new station: `500103065`

## Description
The repository is used to daily release training data for the regular track final project to the learners of the NTU course. 
- Useful Links:
    - Course Website: [from the lecturer's homepage](https://www.csie.ntu.edu.tw/~htlin/course/ml23fall/)
    - Final Project Guildlines: <https://www.csie.ntu.edu.tw/~htlin/course/ml23fall/final/final.pdf>
    - Kaggle competitions: 
        - First Stage: <https://www.kaggle.com/competitions/html2023fall-final>
            - public test period: 2023/10/21 00:00 ~ 2023/10/24 23:40; private test period: 2023/12/04 ~ 2023/12/10; learners must submit predictions before 12/3 23:59
        - Second Stage: <https://www.kaggle.com/competitions/html2023fall-final-project-stage-2>
            - test period: 2023/12/11 00:00 ~ 2023/12/17 23:40; learners must submit predictions before 12/10 23:59
        - Third Stage (tentative): <https://www.kaggle.com/competitions/html2023fall-final-project-stage-3>
            - test period: 2023/12/18 00:00 ~ 2023/12/24 23:40; learners must submit predictions before 12/17 23:59
              
*All timestamp are in UTC+8

## Metadata
- `demographic.json`: file contains demographic information for each station in the following format:
    ```
    {
        sno: the station ID number for each bike station in string
            {
                "sna": the name of the station in Traditional Chinese,
                "sarea": the district of the station in Traditional Chinese,
                "lat": the latitude of the station in float,
                "lng": the longtitude of the station in float,
                "ar": the address of the station in Traditinal Chinese,
                "sareaen": the district of the station in English,
                "aren": the address of the staion in English,
            }
    ...
    }
    ```
- `sno_test_set.txt`: contains the stations' `sno` that needs to predict in the test set
- `release/$date`: directory for all training data, where the `$date` is in YYYYMMDD format
    - in each directory contains `${sno}.json` files, which record the data of each station with number `$sno` of the coresponding date in the following format:
    ```
    {
        timestamp: string in 24-hour format (HH:MM)
            {
                "tot": maximum capacity number of the station at the minute, integers > 0
                "sbi": the current bike amount of the station at the minute, integers >= 0
                "bemp": the number of slots available for parking bikes at the minute, integers >= 0
                "act": whether the station is open to use at the minute, where "1" means open and "0" means prohibited, strings
            }
        ...
    }
    ```
    - we will update `release/` on a daily base.
- `sample_submission_stage${i}.csv`: sample submission for each stage in csv format, e.g.
    ```
    id,sbi
    20231021_500101001_06:40,7.89
    ...
    ```
    The first row of your submission must be `id,sbi`, the following rows must contain 2 columns and seperated by `,`. The first column is the id of your prediction in `YYYYMMDD_${sno}_HH:MM`, where `${sno}` must be one of the station number appears in `sno_test_set.txt`, `YYYYMMDD` indicates the format of date, and `HH:MM` is the format of time. (`Y`=year, `M`=month, `D`=day, `H`=hour, `M`=minute). The second column is your bike amount prediction of the bike station at the given timestamp, it can be integer or float. The number of rows should be equal to **88705**, that is, **1** row of `id,sbi` and **88704** rows of predictions (112 stations $\times$ 3 predictions per hour $\times$ 24 hours $\times$ (4 days in public set period + 7 days in private set period).


For learners that are not familiar with `JSON` format, please refer to <https://en.wikipedia.org/wiki/JSON>.

## How to use
You can use the following commands to get the data, where the latest will be released on a daily frequency.
```
$ git clone git@github.com:hyusterr/html.2023.final.data.git

# use this command to get the latest released data after 13:00 every day
$ git pull
```
If you want to be notified through your GitHub e-mail whenever there is a update in this repository, please click `Watch` on the up-right corner.

For learners who are new to `git` and `Github`, please refer to the tutorials made by the GitHub offical to setting up the environment for yourself.
- Quickstart: <https://docs.github.com/en/get-started/quickstart>
- Generating a new SSH key and adding it to the ssh-agent: <https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent>
