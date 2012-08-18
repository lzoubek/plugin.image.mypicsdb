1) Please translate MyPicsDB into your native language!
==================================================================================
   Files can be found in plugin.image.mypicsdb/resources/language
   Please be aware that the / must be replaced with a \ for Windows!
   Always use the english file to translate!


2) Auto-update  MyPicsDB
==================================================================================
   Idea from Fungify 
   You can call (example for Windows):
   XBMC.RunScript("C:\Users\Name\AppData\Roaming\XBMC\addons\plugin.image.mypicsdb\scanpath.py",--database)
   where Name is the name of the xbmc windows user.
   
   Fungify uses this approach to automatically update MyPicsDB via HTTP API with a cron job.
   wget --directory-prefix=tmp --http-user=<xbmc username> --http-passwd=<xbmc password> "http://Servername:Portnumber/xbmcCmds/xbmcHttp?command=ExecBuiltIn&parameter=XBMC.RunScript("<full path to plugin>\plugin.image.mypicsdb\scanpath.py",--database)

3) For skinners
==================================================================================
  Done by MikeBZH44

a) For skinners, MyPicsDB can be called with following parameters to populate window properties :

  XBMC.RunScript(plugin.image.mypicsdb,0,?action='setproperties'&method ='Latest|Random'&sort ='Shooted|Added'&limit=10)

  Parameters are :

  - action='setproperties' to store in main window properties and in CommonCache DB

  - method='Lastest' to get Latest pictures from DB
  - method='Random' to get random pictures from DB

  - sort='Shooted' to get latest pictures sorted by Shooted date (EXIF DateTimeOriginal)
  - sort='Added' to get latest pictures sorted by Added in DB date (DateAdded)

  - limit=10 to get only 10 pictures

  Properties set to main window (ID=10000) :

  MyPicsDB<Method>.Count = Number of pictures returned (max=limit)
  MyPicsDB<Method>.1.Path = Path to picture #1
  MyPicsDB<Method>.1.Name = Name of picture #1
  MyPicsDB<Method>.1.Folder = Name of picture folder #1
  MyPicsDB<Method>.1.Date = Shooted date of picture #1
  MyPicsDB<Method>.2.Path = Path to picture #2
  MyPicsDB<Method>.2.Name = Name of picture #2
  MyPicsDB<Method>.2.Folder = = Name of picture folder #2
  MyPicsDB<Method>.2.Date = Shooted date of picture #2
  ...
  ...
  ...
  MyPicsDB<Method>.10.Path = Path to picture #10
  MyPicsDB<Method>.10.Name = Name of picture #10
  MyPicsDB<Method>.10.Folder = = Name of picture folder #10
  MyPicsDB<Method>.10.Date = Shooted date of picture #10

  b) To run a slideshow when user clicks on a picture :

  <onclick>XBMC.RunScript(plugin.image.mypicsdb,0,?action='slideshow'&method='Random'&current=1)</onclick>

  Parameters :

  - action='slideshow' to run slide show

  - method='Lastest' to get Latest pictures from DB
  - method='Random' to get Random pictures from DB

  - current=1 to start slideshow with Picture #1  

  c) Statistic properties

  MyPicsDB<Method>.Categories = number of categories in DB
  MyPicsDB<Method>.Collections = number of collections in DB
  MyPicsDB<Method>.Folders = number of folders containing pictures in DB

  MyPicsDBRandom.Categories = MyPicsDBLatest.Categories (same for Count, Collections, Folders) but we don't know wich method each skinner will use so I make the job twice ;)
  