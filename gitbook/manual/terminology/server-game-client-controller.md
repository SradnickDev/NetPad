# Server (Game), Client (Controller)

Server is always a part of your game, takes care of connections and messages. Your game also runs the server, this makes it possible to create a local coop game without much network complexity.

### NetPadPlayer

When a client connects a NetPadPlayer represents the client. Provides the input and allows to share data.

## Client

Client connects to the server. A client is always a controller and provides input or other data for your game. The provided input can then be used to e.g make your ball roll or jump.
