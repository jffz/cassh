CHANGELOG
=========

CASSH Server
-----

1.9.0
-----

2019/05/28

### New Features
  - Generates KRL files by using a database

### Changes
  - /cluster/updatekrl is removed
  - Admin/GET and are removed (it was deprecated)
  - Tests are using random usernames

### Bug Fixes

### Other
  - Add function 'get_pubkey' from database, 'timestamp' and 'get_last_krl'
  - Remove function 'cluster_last_krl', 'cluster_update_krl'

1.8.1
-----

2019/05/28

### Bug Fixes
  - Add wheel into requirements
  - Add build-essential python3-dev dependencies
  - Fix cassh.service


1.8.0
-----

2019/05/27

### New Features
  - Python 3.6 support :
    - remove  __future__
    - use urllib.parse instead of urllib for unquote_plus
    - web.data output in encoded in UTF-8
    - Used .keys() for dict
    - write temporary files in unicode
    - check_output in returning an unicode output

### Changes
  - Python 2.x deprecated
  - Used web.py version 0.40-dev1 instead of 0.39


1.7.3
-----

2019/05/27

### New Features
  - Add debug parameters in configuration

### Changes
  - Use ldap version 3.2.0 instead of 2.5.2 (open => initialize)
  - Edit Dockerfile and requirements.txt
  - Tools: Rename cluster_updatekrl into cluster_update_krl


1.7.2
-----

2019/05/24

### Changes
  - split tools functions in another library


1.7.1
-----

2019/05/23

### Changes
  - always return a Content-Type
  - Block bad realnames (XSS stored)
  - Doesn-t return a blocked username (XSS reflected)

### Bug Fixes
  - Fix some missing http code
  - Fix according tests


1.7.0
-----

2019/05/22

### New Features
  - Add multi-instance (cluster mode), especially to update the KRL
    - ClusterStatus (/cluster/status) : Get the status of the clusted (without auth)
    - ClusterUpdateKRL (/cluster/updatekrl) : Update the current KRL to revoke a user, or get the last version of the KRL inside the cluster
  - Add a User-Agent `HTTP_USER_AGENT : CASSH-SERVER v1.7.0`
  - Add the client version in header `HTTP_SERVER_VERSION : 1.7.0`
  - Add cluster and clustersecret parameters in configuration

### Changes
  - The KRL update is in a separated function
  - HTTP code are not always 200

### Bug Fixes
  - Disable Debug mode (#shame)

### Other
  - More tests, with random ssh-key and username
  - More documentation
