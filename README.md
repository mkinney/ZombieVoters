# OP Banned

They banned me for posting this project.

```
Error: Ban evasion. Your original ban was for violating Global 4 - Personal Information/Invasion/Raid
```

The reason is BS. The project does not contain any personal information.
The only way you can get the information is by paying for an ancestry account.
Even then the social security admin deems the info public enough to let ancestry show it's users.

# Zombie Voter Hunter

A set of scripts that downloads death indexes from ancestry.com. 
Then uses that data to determine if dead people are registered to vote.

## Voter lookup support

### Implemented 

* Michigan

### Investigating

* Georgia
* North Carolina
* Nevada
* Pennsylvania

### Not Possible

* Arizona - [Drivers License or Voter ID # required to look up at](https://my.arizona.vote/WhereToVote.aspx?s=individual&Language=en)

need to add more

## Death data download support

This should work with any county in the country, but I've only tested it thus far with Wayne count MI.

# Setup

```bash
pip3 install -r requirements.txt
cp config.example.json config.json 
```

Edit `config.json` to include your ancestry.com credentials. 

Download chromedriver [for your Chrome version & OS](https://chromedriver.chromium.org/downloads).

Extract the zip and place the binary in the root of the project directory.

# Usage

## Download deaths example

The example below will download death data from the social security death index on ancestry.com.

* -y = the year the social security card was issued
* -p = the page of results to start at, (useful to resume where you left off)
* -c = the county in the sate you are looking into
* -s = the state you are looking into

```bash
./grab_deaths.py -y 1970 -p 1 -c wayne -s michigan
```

## Find zombies

The example below will poll voter registration websites and look up dead people to see if they are registered to vote.
The results will be stored in `output/checked/` there will be two folders. `dead` and `zombies`.
The `zombies` folder contains info on dead people who are registered to vote.

```
./zombie_votes.py --mi
```

In this example we are specifying that we are looking up michigan voters with the `--mi` option.

# Helping & Improvements

If you'd like to help this project would benefit from more regional voter lookups.
It would also benefit from a way to look up deaths that does not require a payed ancestry.com account.
The code is kind of a mess, I wrote this in a few hours to get results ASAP. It could use some polish.
