# CSIE 5043 Machine Learning Final Porject
## Description
The repository is used to release training data daily to the learners of the NTU course. 
- Useful Links:
    - Course Website: [from the lecturer's homepage](https://www.csie.ntu.edu.tw/~htlin/course/ml23fall/)
    - Final Project Guildlines: <TBD>
    - Kaggle competitions:
        - First Stage: <TBD>
            - public test period: 2023/10/21 00:00 ~ 2023/10/24 23:40; private test period: 2023/12/04 ~ 2023/12/10; learners must submit predictions before 12/3 23:59
        - Second Stage: <TBD>
            - test period: 2023/12/11 00:00 ~ 2023/12/17 23:40; learners must submit predictions before 12/10 23:59
        - Third Stage (tentative): <TBD>
            - test period: 2023/12/18 00:00 ~ 2023/12/23 23:40; learners must submit predictions before 12/17 23:59
              
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
- `release/$date`: directory for all training data, where the $date is in YYYYMMDD format
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
