Quake-2-VS2013
==============

Building Quake 2 using Visual Studio 2013

The goal of this project is to build the Quake 2 source code available on id Software's GitHub account in a modern
Visual Studio environment.

The Visual Studio files that come with the source code are hopelessly out of date, and nearly impossible to work with,
even on a Windows XP machine running Visual C++ 6.0. Believe me, I've tried. So rather than continue to wrestle with that,
I have recreated the project instead.

Please go to my website if you would like to watch the videos, or if you have any questions.

http://philipbuuck.com/building-quake-2-with-visual-studio-2013

<strong>This project is the exact same project created in the videos, except for three things.</strong>

First, by default Quake 2 attempts to load the software renderer, and if that doesn't work it throws an error and quits. In order to fix this, go into the \win32\vid_dll.c file. Change line 711 from this:

vid_ref = Cvar_Get ("vid_ref", "soft", CVAR_ARCHIVE);

To this:

vid_ref = Cvar_Get ("vid_ref", "gl", CVAR_ARCHIVE);

Now it will start by trying the OpenGL version of the graphics, which will work.


Second, it is very beneficial to be able to press F5 inside of Visual Studio and run the game from there. One of the Visual Studio options is to set the Working Directory, which is the directory the program thinks it's running in. This defaults to the folder where your quake2 project file is, which is not correct. I have changed this Working Directory to the following value:

"$(SolutionDir)Quake2\"

This ensures that the program is working from the Quake2 directory, which is where the executable is located.

Finally, there were some extra unnecessary files left in that I have deleted. They are:

/quake2.vcxproj.user<br />

/client/asm_i386.h<br />
/client/block8.h<br />
/client/block16.h<br />

/win32/q2.aps<br />
/win32/qe3.ico<br />
/win32/rw_ddraw.c<br />
/win32/rw_dib.c<br />
/win32/rw_imp.c<br />
/win32/rw_win.h<br />
/win32/winquake.aps<br />
/win32/winquake.rc<br />

With this, we now have a game that is ready for distribution.

All the best,<br />
Philip
