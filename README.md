
Questa Applicazione è volta a facilitare i vari addetti allo ScreenSharing nei vari server di fivem/minecraft/rust e dare mezzi per provare il possesso di cheat da parte di utenti sospetti. Da un punto di vista pratico permette di analizzare un determinato file che può essere usato per portarsi vantaggi slealmente, identificare le tracce che può lasciare in un sistema operativo Windows 10/11 in modo da poterlo identificare facilmente quando si andrà a controllare il computer di un utente sospettato di cheating.

![image](https://github.com/Katoylla/String-Extractor/assets/170234034/a94fe9d2-e9ac-418d-b99e-272e4f6ad521)

Una volta importato il file verranno stampate determinate tracce che può lasciare
Funzioni
1) Se il file analizzato contiene un carattere RLO che permette di specchiare tutti i caratteri successivi e "falsificare l'estensione" (l'estensione potrà essere verificata andando sulle proprietà del file) Verra lasciato un avviso come mostrato in foto e segnalata la vera estensione
2) Nome del file: Questa è un informazione molto basilare ma tra le più utili e con più applicazioni (ricerca su qualsiasi processo e/o su tutti gli artifacts di windows, ricerca su disco rigido tramite Everything)
3) Dimensione in Byte: Lascia una stringa utilizzabile direttamente su Everything secondo le opzioni di filtraggio [FAQ](https://www.voidtools.com/support/everything/searching/) (si potrebbe usare il formato size: ma ho deciso di usare size:= per una questione di convenzioni)
4) md5 sha1 sha256 sha512: Tutte possono essere usate con l'[Hasher](https://github.com/EZToolsManuals/EZToolsManuals/blob/main/manuscript/hasher.txt) di Eric Zimmerman e trovare eventuali scan su [VirusTotal](https://www.virustotal.com/gui/home/upload). alcune di queste hanno però applicazioni specifiche, SHA1 può essere usata durante l'analisi del file hive syscache.hve e del file hive Amcache.hve

![image](https://github.com/Katoylla/String-Extractor/assets/170234034/cdf46188-968b-4c00-af54-8b5c180df66a)
![image](https://github.com/Katoylla/String-Extractor/assets/170234034/c1a5fc10-c294-45b8-9ae1-8bb83b6f22df)

5) DPS string. Qui si entra su uno studio più complesso delle tracce che vengono lasciate. La stringa va cercata in un dump del servizio DPS (diagnostic policy service). Poichè questo servizio tra le tante funzioni che ha si occupa di eseguire diagnosi all'apertura di applicazioni e nel farlo utilizza la data di compilazione del .exe aperto salvandolo su memoria ram (sul suo "spazio di indirizzazione virtuale") la troveremo al momento del controllo. Sapendo quindi la data di compilazione del file potremo usarlo come identificatore in caso di eventuale controllo e dare prova dell'esecuzione di quel "cheat".
6) PcaSVC string. Similarmente potremo usare anche un altra traccia che viene lasciata su un altro servizio ovvero PCASvc (Program Compatibility Assistant Service). In questo caso però si utilizza il campo Size of image dell'optional header di un PE trasformato in esadecimale. Questa traccia non è affidabile poichè PCA interagisce solamente con applicazioni con GUI o applicazioni CLI aperte come gui (con doppio click o comando senza parametri) e spesso può non essere lasciata a volta anche quando il file utilizza GUI. 

Riassumendo questa applicazione facilita di molto l'analisi delle tracce lasciate dove possibile ma non è sufficiente per una completa analisi poichè ci sono molte altre tracce da verificare. Un esempio lo sono i domini a cui si connette il PE che vengono lasciati su dnscache e LSASS ma che risulta praticamente Impossibile trovare senza l'utilizzo di sandbox

Nota : Il file potrebbe essere bloccato da windows defender poichè questa versione carica le immagini con una fetch a cdn.discordapp.com
