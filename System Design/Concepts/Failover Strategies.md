Sometimes your database instances may fail entirely which my reduce the performance of your deployment, because of this, it is important to have a backed up, a ready to go instance to take it's place as soon as possible.
### Cold standby

Have a backup of a server or a database being made periodically and using it on the event the main instance fails. 
The backup may be a different machine, so traffic will have to be redirected to the now active backup machine.

**Cons**: Has downside, can lead to some data loss
**Pros**: Simple 

### Warm standby

A constant replication policy makes sure the backup instance is always running and is up to date. In the case of failure, just redirect to the backup machine.

**Cons**: Increased load on the backup service.
**Pros**: Simple

### Hot standby

A constant replication policy makes sure the backup instance is always running and is up to date. The standby is always running and taking Writes and Reads, In the case of failure, just redirect to the backup machine.

**Cons**: Increased load on the backup service.
**Pros**: Simple

### Multi Primary

We a multiple replications of the service that act as the backup, they're always running and are up to date. The standbys are always running and taking Writes and Reads, In the case of failure, just redirect to one of these replicas.

**Cons**: Increased load on the backup service.
**Pros**: Simple