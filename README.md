# Spotify Exploratory Analysis & Music-Recommendation Playlist Creator
## Overview
This project enables the creation of personalized Spotify playlists based on the analysis of top tracks and user preferences. Utilizing the Spotify Web API and the spotipy library, users can generate playlists featuring songs similar to their favorite tracks. Additionally, ngrok is employed to manage OAuth authentication for the Spotify API, providing a seamless and secure way to access and interact with user data.

## Data Collection and Analysis
1. Initial Data Request: The project begins by fetching the top 1000 songs on Spotify using the Spotify API. These tracks are stored and analyzed to provide insights into various musical trends.

2. Data Cleaning and Preparation:
Duplicate tracks are identified and removed to ensure clean data for further analysis.
The tracks are categorized by genre, and specific track features (e.g., tempo, danceability, energy) are retrieved using track IDs.

3. Feature Analysis:
The extracted track features are used to identify trends and patterns related to track popularity. This analysis highlights the characteristics that make tracks popular and identifies similar features across different genres.

## Playlist Creation Based on Favorite Tracks
1. Genre-Specific Track Selection:
After analyzing the top 1000 tracks, favorite songs from specific genres (e.g., house and reggaeton) are extracted for playlist creation.

2. Script to Create Playlists:
A script is developed to generate playlists based on tracks similar to the selected favorite tracks. Using ngrok to handle OAuth authentication, the script securely interacts with the Spotify API to create playlists directly on the user's account.

3. Challenges in Playlist Creation:
Due to the limited number of favorite tracks saved for some genres, the function to retrieve similar tracks could not always generate a full 50 songs for each playlist.
As a result, the house playlist contains 43 tracks, and the reggaeton playlist contains 8 tracks.

## What is ngrok?
ngrok is a tool that creates secure tunnels to your localhost, allowing you to expose a local server to the internet. It provides a public URL that redirects to your local server, which is especially useful for testing webhooks or authentication processes that require a public endpoint. In this project, ngrok is used to set up a public URL for the Spotify OAuth callback, allowing for secure and seamless authentication without exposing your client secrets.

### Key Features
1. Environment Variables:
Sensitive information such as SPOTIPY_CLIENT_ID, SPOTIPY_CLIENT_SECRET, and SPOTIPY_REDIRECT_URI are stored in a .env file and loaded securely using the dotenv library.

2. Playlist Creation:
The program retrieves tracks from two dataframes: fav_tracks_house_3 and fav_tracks_reggaeton_3. It creates two separate playlists on Spotify, each containing 50 songs that are similar to the tracks in the respective dataframes.

3. Track Filtering:
The project ensures that the tracks added to the playlists have an artist popularity  below 75 and track popularity of less than 60, ensuring a curated selection.

4. User-Friendly Output:
Once the playlists are created, the program outputs the URLs of the newly generated playlists and details the tracks added, allowing users to access and enjoy their customized playlists easily.
