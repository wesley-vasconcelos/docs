﻿```sh
docker run -i lacunasoftware/amplia:3.2 -- hash-root-pass -q | docker secret create amplia_root_password_hash -
```