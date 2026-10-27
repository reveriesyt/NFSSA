NFSSA v0.1.0-alpha - Need for Speed: Most Wanted x GTA San Andreas
===================================================================

NFS Most Wanted's own car physics and car rendering, driven inside GTA San
Andreas's world. Both real games run side by side; NFSSA.exe joins them.

This is an ALPHA. Expect rough edges (see "Known limitations").


REQUIREMENTS
------------
* Windows 10 or 11.
* GTA San Andreas, 1.0 US executable (gta_sa.exe).
  The Steam/Rockstar Launcher builds (gta-sa.exe / "3.0") and the Definitive
  Edition are NOT supported. Make a downgraded 1.0 US copy of the game in its
  own folder and leave your original install alone.
* Need for Speed: Most Wanted (2005), speed.exe v1.3, with:
    - ThirteenAG's NFS Most Wanted Widescreen Fix
      (NFSMostWanted.WidescreenFix.asi, from ThirteenAG's WidescreenFixesPack),
      with windowed mode on: in NFSMostWanted.WidescreenFix.ini, under [MISC],
      set WindowedMode = 1 (borderless) or 2 (bordered).
    - An ASI loader for it, e.g. Ultimate ASI Loader as dinput8.dll next to
      speed.exe (the Widescreen Fix download includes one).
  NFSSA does not make NFS MW windowed by itself; without these, MW runs full
  screen and won't combine with GTA SA. NFSSA.exe checks for them and warns.
* An NFS MW career profile with a saved career (the launcher resumes it).

GTA SA needs no extra mods (NFSSA makes it borderless itself). Other SA mods
are fine; some (e.g. SkyGFX) may switch individual NFSSA effects off, as NFSSA
refuses to touch game code another mod has changed.

NFSSA itself needs no ASI loader and never copies files into your game folders.


HOW TO PLAY
-----------
1. Close both games.
2. Run NFSSA.exe.
   The first time, a small setup window asks where your games are: type, paste
   or Browse to your GTA SA 1.0 US folder (the one with gta_sa.exe) and your
   NFS MW folder (the one with speed.exe), then click Continue. NFSSA checks
   that each is a supported version and remembers both, so later runs go
   straight to the NFSSA window. The setup window comes back by itself if a
   remembered folder stops working.
   The NFSSA window shows your folders and options. Change anything you want
   ("Game folders..." to change the install locations), then click
   Start GTA SA. Nothing starts before you click it.
3. GTA San Andreas starts. Load your save.
4. Walk CJ outside (any outdoor spot; not inside a building or interior).
   After about two seconds outdoors, NFS Most Wanted starts by itself and
   walks its own menus into your saved career's free roam.
   (Keep one of the two game windows focused while MW boots.)
5. Once MW's free roam has loaded, the NFS MW window disappears (it keeps
   running, invisibly) and you play in the GTA SA window.
6. Quit GTA SA normally: NFSSA closes NFS MW for you.

The small NFSSA window shows what it is waiting for, and has two options
(remembered for next time):
  * Load NFS MW straight into my career's free roam: on by default. Turn it
    off to go through MW's menus yourself. It applies when MW starts.
      - Career profile: which NFS MW profile it loads. "Most recently saved"
        (the default) picks the one you saved last; or choose one by name.
      - Saves folder: where your NFS MW profiles are. Found automatically:
        Documents\NFS Most Wanted, or the MW game folder if the Widescreen
        Fix's CustomUserFilesDirectoryInGameDir option keeps saves there.
        Browse... picks another folder (each profile is a folder holding a
        save file of the same name); Auto goes back to the detected one.
  * Hide the NFS MW window once free roam has loaded: on by default. MW is
    never hidden before free roam, so you can always see its menus. Untick it
    any time to show the MW window again.
"Start NFS MW now" (available once GTA SA is running) skips the outdoor check. Once MW is hidden, the NFSSA
window minimizes itself. Keep it open: it is what hides MW and closes it
when GTA SA exits (or if NFSSA loses contact with GTA SA for 10 seconds).
Closing it early shows the MW window again and leaves both games running.

If NFSSA finds an older NFSSA install inside a game folder (nfssa_*.asi), it
offers to rename it to *.disabled so the two versions don't run together.


IN-GAME KEYS (either game window)
---------------------------------
  F6   call a police cruiser          F9   LS airport runway drag race
  F7   call a GTO pursuit car              (press again to cancel)
  F8   call a sports cop car           F10  end the pursuit
                                       F11  cops off / on
  Stop in the garage marker outside CJ's house (Grove Street) to open MW's
  safehouse menus (car select, customisation, save).


SETTINGS, LOGS, RESET
---------------------
Everything NFSSA writes lives in %LOCALAPPDATA%\NFSSA :
  nfssa.ini           your settings (edit with Notepad; restart to apply)
  nfssa.default.ini   the shipped defaults, for reference
  launcher.ini        the remembered game folders and launcher options
  logs\               nfssa_launcher.log, nfssa_gtasa.log, nfssa_nfsmw.log
  runtime\            the modules NFSSA.exe loads into the games

  NFSSA.exe --setup          open the setup window straight away (the same as
                             "Game folders..." in the NFSSA window)
  NFSSA.exe --check          show the remembered game folders and check the
                             NFS MW Widescreen Fix setup, then exit
  NFSSA.exe --reset          forget the remembered game folders
  NFSSA.exe --reset-config   restore nfssa.ini to the defaults

Uninstall: delete NFSSA.exe and the %LOCALAPPDATA%\NFSSA folder. If NFSSA
renamed an old module to *.disabled, you can delete that file too.


KNOWN LIMITATIONS
-----------------
* Alpha build: many parts have only been tested by the developer on one PC.
* The MW menu autostart only presses keys on menu screens it knows. On any
  other screen or dialog it stops and hands control to you; finish the menus
  by hand (Career > Resume Career > Resume Free Roam).
* Antivirus software may flag NFSSA.exe because it loads its module into the
  games the same way mod loaders and trainers do.


TROUBLESHOOTING
---------------
* "not a version NFSSA supports": the folder you picked has another version.
  Check that gta_sa.exe (with an underscore) is the 1.0 US one, and that
  speed.exe is v1.3.
* MW starts but stays in its menus: the NFSSA window says whether it found
  career profiles. Check the Saves folder (Browse...) and Career profile.
  nfssa_nfsmw.log names the folder and profile it used ("autostart:" lines).
* MW never starts: make sure CJ is outdoors and the pause menu is closed. The
  NFSSA window says what it is waiting for; nfssa_gtasa.log has details.
* "NFS Most Wanted is not set up the way NFSSA needs": install the Widescreen
  Fix and its ASI loader, and turn on WindowedMode (see REQUIREMENTS).
* The NFS MW window is invisible and NFSSA is no longer running (e.g. it was
  ended in Task Manager): close NFS MW from Task Manager (speed.exe).
* If MW stops drawing while hidden, NFSSA shows its window again by itself.

