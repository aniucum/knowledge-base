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

#### How to rebuild the Admin - Compact blobstore deletions index file if soft-deleted blobs are orphaned
https://support.sonatype.com/hc/en-us/articles/360025325653-How-to-rebuild-the-Admin-Compact-blobstore-deletions-index-file-if-soft-deleted-blobs-are-orphaned
Add the following line to the `metadata.properties` file in the root directory of the blobstore.
```bash
rebuildDeletedBlobIndex=true
```
