This script will ask you if you wish to try again after each run. Type in any  
character other than `y` or `Y` to exit at this point.  

### Summary  
  
`Sinon` is a game of timing, the goal is to eliminate all enemies in  
under one minute.  
  
To start, compile and run the sinonram. To resume, compile and run the  
output repeatedly until you have won/lost the game. For example:  
  
``` <!---sh-->  
    cp sinon.c run.c  
    gcc -O0 run.c -o run && ./run | tee run.c  
    gcc -O2 run.c -o run && ./run | tee run.c  
    ...  
```  
  
### Remarks  
  
`Sinon` is played by compiling and running the output repeatedly. Two  
factors determine what actions are taken:  
  
+ Time since last compilation.  
+ Whether compiler optimizations are enabled or not.  
  
If you fire too quickly, the weapon will jam. If you fire too slowly,  
you will not be able to eliminate all the enemies in time. Thus the  
primary objective of the game is to time your compilations just right.  
  
`Sinon` has two weapons that are selected based on compiler optimization  
level:  
  
+ "gcc -O2" or "clang -O2" will fire Hecate II, a powerful rifle that  
  requires longer time to cool off.  
  
+ "gcc -O0" or "clang -O0" will fire Glock 18C, a less powerful pistol  
  that requires less time to cool off.  
  
Because the weapons cool off independently, the best strategy is to  
alternate between the two weapons. It is fairly easy to win the game  
with this strategy even with occasional jams.  
  
If your compiler does not have the right optimizations, only Glock 18C  
would be available. It is still possible to win, but your timing will  
need to be more precise. This is effectively playing the game on  
"hard" mode. It is worth trying this mode even if you have the right  
compilers.  
  
### Compatibility  
  
`Sinon` has been tested and verified to work on these platforms:  
  
+ gcc 4.4.3 on Linux.  
+ gcc 4.4.5 on Linux.  
+ gcc 4.8.2 on Linux.  
+ gcc 4.8.3 on Cygwin/MingW.  
+ clang 3.4-1 on Linux.  
+ clang 3.4.2 on Cygwin.  
+ gcc 4.3.5 on JS/Linux (playable but likely unwinnable, because it  
  takes too long to compile).  
+ tcc 0.9.25 on JS/Linux (no optimization, so only "hard" mode is  
  available).  
  
`Sinon` is intended to be played in a 80x25 terminal.  
  
### Miscellaneous features  
  
`Sinon` might be the first game that uses compiler optimization level as  
a primary input.  
  
`Sinon` has a demo mode that plays the game automatically. Make sure  
that there are no files named "run" and "run.c" in current directory  
(they will be overwritten) and run:  
  
``` <!---sh-->  
    perl sinon.c | bash  
```  
  