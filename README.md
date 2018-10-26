# mongoDB-taskDefinition

Dette er taskdefinition til MongoDB-databasene våre. De kjører i ett eget Data-cluster. Som du ser så blir de
mountet på disk til clusteret som gjør at du får persistens selv om du restarter docker-containerern. I tilegg blir de backet opp
av [https://github.com/bekk/bekk-scheduledTask-mongo-s3-backup](https://github.com/bekk/bekk-scheduledTask-mongo-s3-backup)

Jeg har opplevd at man må starte servicen to ganger
for at det skal fungere ordentlig. 

## Restore av mongo-databasene

Hvordan du gjør det står beskrevet [https://developer.bekk.no/docs/dump-og-restore-av-mongodatabase](https://developer.bekk.no/docs/dump-og-restore-av-mongodatabase)

Når du har restoret databasene må du også opprette brukerene på nytt: 

1. Logg deg inn på databasen: `mongo --username alice --password --authenticationDatabase admin --host mongodb0.examples.com --port 28015`

1. Opprett brukeren
   
    ```
   use admin
   db.createUser(
      {
        user: "Invoice",
        pwd: "[PASSORD]",
   		roles: [ {role: "readWrite", db: "Invoice" } ]
      }
   );
   
    ```
   
  

                                                                                                     
                                                                                                   
                                                                                                     