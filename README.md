<!---
license: Licensed to the Apache Software Foundation (ASF) under one
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

# cordova-plugin-mg-kunder-keychain

This cordova plugin enables you to use iOS Keychain to manage accounts of one user and share with other applications of the same company (e.g google apps like gmail, youtube, etc).

It's possible to moddify this plugins to allow multiple accounts.

By default, this plugin cypher the key and message before setting data into Account Manager with AES 256 bits (Android only).


## Account Manager settings

The following variables need to be set in config.xml:
- ACCOUNT_MANAGER_LABEL
- ACCOUNT_MANAGER_TYPE

## Supported Platforms

- Android
- iOS

## Methods

- initWithKey: register the encryptionKey for AES encryption. It must be called before other Account Manager methods
* function(encryptionKey, successCallback, errorCallback) 
- registerAccount: register an user in Account Manager
* function(userName, password, accountType, group, userData, successCallback, errorCallback) 
- removeAccount: remove all data from keychain (iOS)
* function(accountType, successCallback, errorCallback) 
- getUserAccount: returns an String with account name if account exist
* function(accountType, group, returnKey, successCallback, errorCallback) 
- getPassword: returns password if account exist
* function(accountType, group, key, successCallback, errorCallback) 
- getDataFromKey: returns data from specified key
* function(accountType, group, key, successCallback, errorCallback) 
- setUserData: set object with information into Account Manager or Keychain
* function(accountType, group, data, successCallback, errorCallback)
- setPassword: update account password
* function(accountType, group, newPassword, successCallback, errorCallback) 
- resetPassword: update account password with String "0000"
* function(accountType, group, successCallback, errorCallback) 

## Key Parameters

- accountType: the same account type unique identifier set in config.xml file
- group (Nullable): group identifier. Only for iOS shared keychain
- data: key-value object
- encryptionKey: the key used to encrypt/decrypt key and value data. 

## Notes

- You can not delete user data from Account Manager. Use "setUserData" to change value to empty.
- You can delete account from Account Manager.
- removeAccount remove all keychain data from your app.
- You can not set user data to Account Manager if it doesn't have an account for your identifier.

## License

MIT

