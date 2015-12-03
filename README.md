# spotify-import

### 1. Get your Rdio data

Alex Hanson created a solid tool for exporting Rdio data. Find it [here](https://github.com/alexhanson/rdio-export). One of the outputs of this tool is an `albums.ndjson` file. Store this in a memorable location on your computer – this program will require it.

### 2. Create a Spotify app for development

- Go to the [Spotify Developer Wesite](https://developer.spotify.com/my-applications) and click "Create an App" in the button in the top right.
- Choose any title / description. I put "SpotifyImport" as my title.

### 3. Get an access token

Probably the easiest way to do this is the following:
- Add http://localhost:8888 as a `uri_redirect` on your app management page.
- Go to this URL: https://accounts.spotify.com/en/authorize?client_id=YOUR_CLIENT_ID&redirect_uri=http:%2F%2Flocalhost:8888%2Fcallback&scope=user-library-modify&response_type=token&state=123
- You'll be redirected to the `localhost` page, but your access token (`access_token`) will be in the URL. Copy that.

### 4. Download the project and initialize
- `$ git clone https://github.com/knappg/spotify-import.git`
- `$ cd spotify-import`
- `$ npm install`

### 5. Run and follow the prompts
- `$ ./import`
