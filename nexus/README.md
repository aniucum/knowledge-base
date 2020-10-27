#### nexus
#####################
1. Shut down Nexus
2. Make a backup of /nexus-data/db
3. Run: java -jar $INSTALL_DIR/lib/support/nexus-orient-console.jar
4. At the orientdb prompt run the following:
   1. connect plocal:/nexus-data/db/component/ admin admin
   2. repair database --fix-links
   3. rebuild index *
   4. disconnect
   5. exit
    
