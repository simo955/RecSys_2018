# Recommender System 2018 Competition

## Project Overview

This competition aggregated the results of 4 different submissions on *Kaggle* ([here](https://www.kaggle.com/c/recommender-system-2018-challenge-polimi/overview)) over a time span of 6 months.<br/>
The goal was to produce a recommendation of 10 tracks for each of the 10k given playlists. 
Independently built a **Hybrid Recommender System** combining both content-based filtering and collaborative filtering techniques using python.  <br/>
*Final position*: 12th over 80 teams (for 3 submissions in the top 5 reaching highest possible evaluation).

## Goal

The application domain is a music streaming service, where users listen to tracks (songs) and create playlists of favorite songs. The main goal of the competition is to discover which track a user will likely add to a playlist, therefore "continuing" the playlist.

## Challenge description

- The dataset includes around 1.2M interactions (tracks belonging to a playlist) with 50k playlists and 20k items (tracks)
- A subset of 10k playlists has been selected as target playlists
- The goal is to recommend a list of 10 relevant tracks for each target playlist
- Target playlists are divided into two groups of 5k playlists each (see the Data tab for a more accurate description):
  - Playlists in the first group are sequential: for these playlists, tracks in the training set are provided in sequential order
  - Playlists in the second group are random: for these playlists, tracks in the training set are provided in random order
- MAP@10 is used for evaluation
- It is possible to use any kind of recommender algorithm you wish (e.g., collaborative-filtering, content-based, hybrid, etc.) written Python or R

# Evaluation
According to the standing, for each deadline points will be assigned to the teams in the following manner:

$$ si = 12 - 12 \times \log2{ \left [ \frac{ri - 1}{N\textrm{teams} - 1} +1 \right ] } $$

where *i* is the deadline, <br/>
*Nteams* = number of teams in the competions, <br/>
*ri* = ranking of the team in the leaderboard at deadline (i = 1..*Nteams*) <br/>

Maximum standing vote is 12 points.

## Final score

The total score is computed from the private leaderboard with the following formula:

$$ \textrm{score} = \frac{ \sum{i} wi \cdot si }{\sum{i} w_i} + b + t + a $$

where i is the i-th deadline, and

$$ wi = 1 \textrm{ (intermediate deadline)}
wi = 2 \textrm{ (final deadline)} $$

The last deadline weights twice each intermediate deadline.

Maximum final score is 33.5 points.

Attention. Results on the public leaderboard are computed on a different subset of the test set, so it may differ from the private one.


## Data description

> IMPORTANT: All files are comma-separated (columns are separated with ',' ) - including the submission file.

### List of files: 

- **train.csv**: the training set describing which tracks are included in the playlists
- **tracks.csv**: supplementary information about tracks
- **target_playlists.csv**: the set of target playlists that will receive recommendations
- **train_sequential.csv**: list of ordered interactions for the 5k sequential playlists. You can find the file here.
- **sample_submission.csv**: correct format for submissions

### train.csv
- **playlist_id**: identifier of the playlist
- **track_id**: identifier of the track
All tracks within a playlist are in random order, except for the 5000 ordered target playlists (see target_playlists.csv).

### target_playlists.csv
- **playlist_id**: identifier of the playlist that will receive recommendations. The file contains a list of 10k playlists.
  - The first 5k target playlists (from playlist_id=7 to playlist_id=50431) are sequential. For each of these playlists, the order of tracks in train_sequential.csv corresponds to the order inside the playlist. You can find the file here and the topic here
  - The last 5k target playlists (from playlist_id=3 to playlist_id=50424) are random. For each of these playlists, the order of tracks in train.csv is random and does not generally corresponds to the order inside the playlist. The same is for all other playlists in train.csv.

### tracks.csv
- **track_id**: unique identifier of the track
- **valbum_id**: unique identifier of the album
- **artist_id**: unique identifier of the artist
- **duration_sec**: duration of the song in seconds

### train_sequential.csv
- **playlist_id**: identifier of the sequential playlist
- **track_id**: identifier of the track

### sample_submission.csv
A sample submission file in the correct format: [playlist], [ordered list of recommended items]

```
playlist_id,track_ids
3,0 1 2 3 4 5 6 7 8 9 
6,0 1 2 3 4 5 6 7 8 9
[ . . . ]
50428,0 1 2 3 4 5 6 7 8 9
50431,0 1 2 3 4 5 6 7 8 9
```

> IMPORTANT: first line is mandatory and must be properly formatted.