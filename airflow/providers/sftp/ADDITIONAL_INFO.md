<!--
 Licensed to the Apache Software Foundation (ASF) under one
 or more contributor license agreements.  See the NOTICE file
 distributed with this work for additional information
 regarding copyright ownership.  The ASF licenses this file
 to you under the Apache License, Version 2.0 (the
 "License"); you may not use this file except in compliance
 with the License.  You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing,
 software distributed under the License is distributed on an
 "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 KIND, either express or implied.  See the License for the
 specific language governing permissions and limitations
 under the License.
 -->

## Release 2021.3.3

### Features

#### SFTP connection ``private_key_pass`` extra param is renamed to ``private_key_passphrase``

Some operators perform SFTP operations by the means of `SFTPHook`. `SFTPHook` delegates the actual SFTP connection to
the `pysftp` module.

When connecting with a private key protected by a passphrase, the `private_key_pass` extra parameter had to be
specified in the connection, and this corresponded to the arguments' naming in `pysftp`.

However, `SFTPHook` inherits from `SSHHook` which already manages a `private_key_passphrase` extra param. But this
param was unused in favor of the `private_key_pass` param introduced in `SFTPHook`.

For consistency, `private_key_pass` has been dropped in `SFTPHook` and `private_key_passphrase` is well reused.
This may require updating your SSH connections used to do SFTP.

### Bug fixes

* `Corrections in docs and tools after releasing provider RCs (#14082)`

## Release 2021.2.5

### Features

* `Add retryer to SFTP hook connection (#13065)`
