# spotify-import

_Warning! This program is a work in progress and is still working through some bugs. I'll remove this when it's fully functioning. View the issues section for more details._

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

### Issues

- _The program hits the rate limit just about immediately._ Spotify doesn't really like you hammering their search api, so we need to find a way to throttle it. I attempted to throw in some sleep calls, but there's something up with those too.

- _Many albums are not found._ I'm preferring to search by UPC if we have it, but it seems like it's not finding it regardless. There may be an issue with the way that `unirest` is serializing the query parameters with its `.query` call, but it requires some more fine-tuned testing.
