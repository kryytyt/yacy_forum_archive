En:DebianInstall
================

Date: 2014-05-28 18:21:30

[Installation of YaCy on Debian: ]{.autocomment} Java 7

← Nächstältere Version

Version vom 28. Mai 2014, 16:21 Uhr

Zeile 17:

Zeile 17:

 

<div>

And finally install YaCy itself

</div>

 

<div>

And finally install YaCy itself

</div>

 

<div>

  apt-get update

</div>

 

<div>

  apt-get update

</div>

−

<div>

  apt-get install openjdk-~~6~~-jre-headless \# java 6 is sufficient,
only a headless version is needed

</div>

\+

<div>

  apt-get install openjdk-[7]{.underline}-jre-headless \# java 6 is
sufficient, only a headless version is needed

</div>

 

<div>

  apt-get install yacy

</div>

 

<div>

  apt-get install yacy

</div>

 

 