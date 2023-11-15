## **Challenge**- babygame01

We are givena game file and a netcat command to connect to the game via terminal. The game displays: 'win' upon reaching the last place i.e 29,89 in the 2d space. However this does not give us the flag. 

On opening the file in ghidra, in the main function it seems that the local_aac and the local_aa8 variable holds the place of the @ in the 2d space(written in hex) which different while loops is making sure to continue the game till 29,89 co-ordinates is reached.  ![Screenshot 2023-11-15 123638](https://github.com/Hackurman01/ctp-2/assets/144946633/e23d47ea-b2c2-4697-a93f-b0e9304245b9) 
![image](https://github.com/Hackurman01/ctp-2/assets/144946633/aa457c64-a33e-4de0-9a59-dec39a7fc437)

Below in the lines of code we see an if condition where upon it not being null  a win function is called after a string: "flage". The init_player() function defines the initial position of the player at 4,4.
The init_map() function states how the map would look like with each input from the user. 
The nested do loops is the iteration of the game after every input: It first gets the character from the user moves_player moves the @ accordingly.
The move_player function shows us the different use of the w,a,s and d characters. Also it has different characters with use cases like : l with a character allows us to change the player_tile to that character . p would generate a solve round function. Putting p in the game we automatically get to the last tile. ![image](https://github.com/Hackurman01/ctp-2/assets/144946633/5a7e26c9-b1b3-4f50-9a74-d02ff05cbfc2)


Still this does not give us the flag.
