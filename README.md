This role is not completely self-sufficient.  After initial deployment,
the database must be populated.  Start by creating an admin account,
then use the admin account to create more accounts.

Example, assuming host synapse is the KDC:

    ansible@synapse:~ $ sudo kadmin.local
    Authenticating as principal root/admin@NEURONPOINTER.NET with password.
    kadmin.local:  listprincs
    K/M@NEURONPOINTER.NET
    kadmin/admin@NEURONPOINTER.NET
    kadmin/changepw@NEURONPOINTER.NET
    kadmin/synapse@NEURONPOINTER.NET
    kiprop/synapse@NEURONPOINTER.NET
    krbtgt/NEURONPOINTER.NET@NEURONPOINTER.NET
    kadmin.local:  addprinc aaron/admin
    WARNING: no policy specified for aaron/admin@NEURONPOINTER.NET; defaulting to no policy
    Enter password for principal "aaron/admin@NEURONPOINTER.NET":
    Re-enter password for principal "aaron/admin@NEURONPOINTER.NET":
    Principal "aaron/admin@NEURONPOINTER.NET" created.
    kadmin.local:  quit
    ansible@synapse:~ $

    0 aaron@mawg:~ $ pass show aaron/kerberos/aaron\_admin

    0 aaron@mawg:~/control_center/ansible $ kadmin -p aaron/admin
    Authenticating as principal aaron/admin with password.
    Password for aaron/admin@NEURONPOINTER.NET:
    kadmin:  addprinc aaron
    WARNING: no policy specified for aaron@NEURONPOINTER.NET; defaulting to no policy
    Enter password for principal "aaron@NEURONPOINTER.NET":
    Re-enter password for principal "aaron@NEURONPOINTER.NET":
    Principal "aaron@NEURONPOINTER.NET" created.
    kadmin:  quit
    0 aaron@mawg:~/control_center/ansible $

    0 aaron@mawg:~ $ pass show aaron/kerberos/aaron

