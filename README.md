# SimpleChat

A multi-client console chat application in Java, built on the OCSF (Object Client Server Framework) from *Object-Oriented Software Engineering* (Lethbridge & Laganière). Written for SEG2105.

## Features

- Clients log in with a unique-per-connection login ID; the server prefixes broadcasts with it.
- Server broadcasts any message typed on the server console.
- Console commands on both sides for managing the connection (see below).

## Requirements

Java 17+ (developed on Java 21).

## Build

```sh
mkdir -p out
javac -d out $(find OCSF/src src -name '*.java')
```

## Run

Start the server (default port 5555):

```sh
java -cp out edu.seg2105.server.backend.EchoServer [port]
```

Start one or more clients:

```sh
java -cp out edu.seg2105.client.ui.ClientConsole <loginId> [host] [port]
```

## Commands

Client:

| Command | Effect |
| --- | --- |
| `#quit` | Disconnect and exit |
| `#logoff` | Disconnect without exiting |
| `#login` | Reconnect after `#logoff` |
| `#sethost <host>` / `#setport <port>` | Change target host or port |
| `#gethost` / `#getport` | Show current target |

Server:

| Command | Effect |
| --- | --- |
| `#quit` | Close the server and exit |
| `#stop` | Stop accepting new clients |
| `#close` | Stop listening and disconnect all clients |
| `#start` | Resume listening |
| `#setport <port>` | Change port (only while closed) |
| `#getport` | Show current port |

## Layout

```
OCSF/src/            OCSF framework (AbstractClient, AbstractServer, ConnectionToClient)
src/edu/seg2105/
  client/backend/    ChatClient
  client/common/     ChatIF
  client/ui/         ClientConsole
  server/backend/    EchoServer, ServerConsole
docs/Test-Cases.docx
```
