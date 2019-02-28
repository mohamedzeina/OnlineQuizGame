# OnlineQuizGame
**Application is implemented in C#**

A client-server application which will operate as a simple quiz game. The application consists of two separate modules. 
First module is the client module in which players will be able to enroll to an open quiz game and will be able to play with other players.

Second Module is the server module in which the server acts as a facilitator. It handles incoming connections from players and helps players communicate so that they can participate in a quiz game and play it properly. Also, the server keeps scores during the game and broadcasts the results of the game when the quiz game is finished.

The server listens on a predefined port and accepts incoming client connections. One or more clients can connect to the server at the same time. Each client knows the IP address and the listening port of the server (to be entered through the GUI).

Clients connect to server on corresponding port and identify themselves with their names. Server keeps the names of currently connected clients in order to avoid the same name to be connected more than once at a given time to the server.




Server Specifications:
---
* There is only one server running on this system.
* The port number on which the server listens is not hardcoded; it is taken from the Server GUI.
* The server starts listening on the specified port. It handles multiple clients simultaneously.
* All activities of the server are reported using a rich text box on the Server GUI including names of connected clients as well as all the received questions, answers and the status of each turn (the player got the answer right/wrong).
* When the server application is closed (even abruptly), program doesn't crash.



Client Specifications:
---
* The server IP address and the port number are nothardcoded and are entered via the Client GUI.
* If the server or the client application closes, the other party understands disconnection and acts accordingly.
* All activities of the client are reported using a rich text box on the Client GUI including connection information, send/received question and answers as well as status of each turn.
* Each client must have a name. This name is entered using the Client GUI. This name is also sent to the server. The server identifies the clients using their names. Each client must have a unique username.
* Each client can disconnect from the system at any time. Disconnection can be done by pressing a button on Client GUI or just closing the client window.
* Both connection and message transfer operations are performed using TCP sockets.





Manual:
---

1. Game starts only when the start game button is clicked on Server GUI. There must be at least two clients connected in order to start the game.
2. The players of the game are the ones who successfully connected when start game button is clicked. After that point, new players won't be able to connect to the server and join the game. Though, the players in the game can disconnect at their will and this doesn't cause the program to crash.
3. The players turns are in order of the one with the smallest alphabetical name. The first player is the one with alphabetically smallest name. 
4. Game is played in Round Robin fashion. This means that each player asks exactly once in each round and answers all of the other players’ questions.
5. The server sends a "ask question" command to the player in turn
6. The player who receives this command, sends his/her question and the corresponding correct answer to the server.
7. The server receives both the question and the correct answer.
8. The server sends the question to the other players.
9. Other players receive the question and send their answer to that question to the server.
10. The server receives the other players' answers and checks if it matches with the correct answer provided by the asking player.
11. The result of the above check (correct answer or wrong answer) is sent to both players by the server.
12. Server keeps scores of each player. Each correct answer means 1 point and false answer means 0 points. The score table is sent to all players after each question.
13. When the game is finished, the server broadcasts these results to every connected player and announces the winner. The game will normally end when it has played number of rounds rounds provided before the game starts. However, at any point during the game, if there is only one connected player remaining, the server announces that player as the winner and finish the game
