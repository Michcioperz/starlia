# Starlia

Starlia is an RSS/Atom feed reader for people with a different understanding of _usability_.

## Architecture design

The fetching process converts the posts' content to Markdown and the metadata to an email-like format in a bid to make readability in the terminal pretty okay at low effort.

There shall be multiple modes of operation available to the user, with different ways of fetching the feed updates. The modes shall be various combinations of heavy/light/no server and heavy/light client.

The server regularly updates the feeds and stores them. In the light mode, the feed history is not kept, only the most recent posts. This can prove counter-intuitive when the subscribed feeds change rapidly throughout the day (for example, the Github activity feed or a social network feed such as Mastodon's). Therefore in the heavy mode, the feed history is stored indefinitely, with the option for the user to purge the cache.

The difference between heavy and light mode on the client side is also in the storage mechanisms. The light client shall only store the access credentials to the server and perform all actions remotely without fetching too much. This mode, however, depends heavily on network connection and its quality, rendering it useless in travel (specifically - on Polish trains where the mobile reception is extremely weak). That is where the heavy client mode comes in, pulling all the necessary content from the server, as well as fetching the images and potentially the excerpts of other linked articles and such things.

The modes described so far require running the server software somewhere. It shall be possible though, due to the amount of code being shared between the client and the server, to run Starlia in a serverless mode, where the client software handles the server's work.
