## **Challenge**- babygame01

We are givena game file and a netcat command to connect to the game via terminal. The game displays: 'win' upon reaching the last place i.e 29,89 in the 2d space. However this does not give us the flag. 

On opening the file in ghidra, in the main function it seems that the local_aac and the local_aa8 variable holds the place of the @ in the 2d space(written in hex) which different while loops is making sure to continue the game till 29,89 co-ordinates is reached.  ![Screenshot 2023-11-15 123638](https://github.com/Hackurman01/ctp-2/assets/144946633/e23d47ea-b2c2-4697-a93f-b0e9304245b9) 
![image](https://github.com/Hackurman01/ctp-2/assets/144946633/aa457c64-a33e-4de0-9a59-dec39a7fc437)
![Screenshot 2023-11-15 130357](https://github.com/Hackurman01/ctp-2/assets/144946633/c94fb672-d556-4e12-95a0-3da8231d156b)

