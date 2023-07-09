<h1 align="center"> Tune2Tube </h1>

<p align="center">
  <img src="./tune2tube.png" alt="logo"  width="300" height="200">
</p>
<p align="center">
    <a href="https://github.com/yogeshwaran01/spotify-playlist-to-youtube-playlist/stargazers"><img alt="GitHub stars" src="https://img.shields.io/github/stars/yogeshwaran01/spotify-playlist-to-youtube-playlist"></a>
    <a href="https://github.com/yogeshwaran01/spotify-playlist-to-youtube-playlist/network">
    <img alt="GitHub forks" src="https://img.shields.io/github/forks/yogeshwaran01/spotify-playlist-to-youtube-playlist"></a>
    <a href="https://github.com/yogeshwaran01/spotify-playlist-to-youtube-playlist/blob/master/LICENSE.txt">
    <img alt="GitHub license" src="https://img.shields.io/github/license/yogeshwaran01/spotify-playlist-to-youtube-playlist?color=blue"/>
    </a>
    <a href="https://github.com/psf/black">
    <img alt="Code style" src="https://img.shields.io/badge/codestyle-Black-blue"/>
    </a>
    <img alt="GitHub Repo size" src="https://img.shields.io/github/repo-size/yogeshwaran01/spotify-playlist-to-youtube-playlist"/>
</p>

<p align="center">From Spotify's Groove to YouTube's Show: Seamless Conversion! </p>

## About

A simple python script to convert your Spotify playlist into YouTube playlist.

### Features

- Create a YouTube Playlist from Spotify playlist
- Sync a YouTube Playliset with Spotify playlist
- Sync multiple Playlists

## Setup

### Google-Youtube

1. Go to Google Cloud Console (console.cloud.google.com), sign in, and create a new project.
2. Select New Project project created from project dropdown menu in the top navigation bar.
3. Go to the Credentials page in the "API & Services" section (console.cloud.google.com.apis/credentials?projectID) of the left sidebar.
4. Click "Create Credentials" and select "OAuth client ID".
5. After creating select edit button in the OAuth 2.0 Client IDs, Select application type as Desktop App and then click create.
6. Click the download button to download the credentials in your project directory. Rename the file to `client_secret.json`
7. Go to the OAuth consent screen in the API & Services section of the left sidebar. Under test user add your Gmail id.

### Spotify

1. Go to the Spotify Developer Dashboard and log in with your Spotify account.
2. Click on the "Create an App" button and fill out the necessary information, such as the name and description of your application.
3. Once you've created the app, you'll be taken to the app dashboard. Here, you'll find your client ID and client secret, which are used to authenticate your application with the Spotify API.
4. Add you client id and secert in `.env` file

```env
CLIENT_ID="xxxxxxxxxxxxxxxxxx"
CLIENT_SECRET="xxxxxxxxxxxxxxxx"
```

## Installation

1. Install Python (python.org)

2. Install required package

```bash
pip install -r requirements.txt
```

## Usage

- [Create a new YouTube playlist from Spotify playlist](#create-a-youtube-playlist-from-spotify-playlist)
- [Sync YouTube playlist with spotify playlist](#sync-your-youtube-playlist-with-your-spotify-playlist)
- [Sync multiple playlists](#sync-multiple-playlist)

### Format

```
main.py create [OPTIONS] SPOTIFY_PLAYLIST_ID
```

### Example

#### Create a YouTube Playlist from Spotify Playlist

```bash
python main.py create SPOTIFY_PLAYLIST_ID
```

#### Options

```txt
  --public                Create a public playlist
  --private               Create a public playlist
  -n, --name TEXT         Name of the YouTube playlist to be created
  -d, --description TEXT  Description of the playlist
  -l, --only-link         just only link of playlist, logs not appear
  -s, --save-to-sync      Save to list of playlist to sync
  --help                  Show this message and exit.  
```

Google OAuth link will open browser for authorization. Sign-in into account.

#### Examples

- Create a public YouTube playlist with a custom name and description:

```bash
python main.py create --public -n "My Playlist" -d "A collection of my favorite songs" SPOTIFY_PLAYLIST_ID
```

- Create a private YouTube playlist and save it to the list of playlists to sync:

```bash
python main.py create --private -s SPOTIFY_PLAYLIST_ID
```

- Get only the link of the YouTube playlist without displaying logs:

```bash
python main.py create -l SPOTIFY_PLAYLIST_ID
```

#### Sync Spotify and YouTube playlist

```txt
Usage: main.py sync [OPTIONS]

  Sync your YouTube playlist with Spotify Playlist

Options:
  -s, --spotify_playlist_id TEXT  Spotify playlist ID
  -y, --youtube_playlist_id TEXT  YouTube playlist ID
  -l, --only-link                 just only link of playlist, logs not appear
  --help                          Show this message and exit.
```

```bash
python main.py sync -s <spotify_playlist_id> -y <youtube_playlist_id>
```

- `-s`, `--spotify_playlist_id`: Specifies the Spotify playlist ID to sync.
- `-y`, `--youtube_playlist_id`: Specifies the YouTube playlist ID to sync.
- `-l`, `--only-link`: Retrieves only the link of the playlist without displaying logs.

It alson open the browser for authorization. Sign up with your google account to sync playlist.

Sync a Spotify playlist with a YouTube playlist and retrieve only the link:

```bash
python main.py sync -s SPOTIFY_PLAYLIST_ID -y YOUTUBE_PLAYLIST_ID --only-link
```

#### Sync Multiple playlist

When creating a playlist, just add `--save-to-sync` or `-s` flag to it. It save the Spotify and YouTube playlist id in [playlists.json](https://github.com/yogeshwaran01/spotify-playlist-to-youtube-playlist/blob/master/playlists.json) file.

When you need to sync it, just run

```bash
python main.py sync
```

It will sync all the playlists in that file.

To clear that file just run,

```bash
python main.py clear
```

### How this works

Refer [this](https://dev.to/yogeshwaran01/from-spotify-to-youtube-how-i-built-a-python-script-to-convert-playlists-2h89) blog post for more info

### Contact Me

If you need more info or any support please feel free to contact [me](mailto:yogeshin247@gmail.com)

### Contributing

Contributions are welcome! If you have any ideas, suggestions, or bug reports, please open an issue or submit a pull request.

### License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/yogeshwaran01/spotify-playlist-to-youtube-playlist/blob/master/LICENSE) file for details.
