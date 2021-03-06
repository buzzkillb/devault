This release includes the following features and fixes since 1.1.7 release:

This release includes the following features and fixes:

 - Support for BLS based transactions
   - Add Chia's BLS library files and Relic source code
   - Chaining transactions currently not allowed for BLS transactions
   - Chaining transaction limits enabled by default
   - Hard fork will be on October 10, 2020 (4pm GMT) to enable these transactions
   - Allows transactions to be aggregated in a block with one aggregate signature
   - Wallet support will be in a future release
 - Compile/build support for Mac versions 10.14 or higher only
   - Autotools build no longer available. CMake must be used for compilation
   - Minimum Cmake version is 3.12
   
 - Minor bug fixes and improvements.
 - Add a dumpphrase RPC command so devaultd users can easily check 12/24 word phrase
 - seedphrase command line option disabled for QT wallets
 - When restoring wallet with -seedphrase from command line, allow restoring legacy addresses after BLS becomes default
 - Support for Qt 5.15 builds
 - Disable dumping rewards logfile
 - Protocol version bumped to 70022
 - New `fees` field introduced in `getrawmempool`, `getmempoolancestors`,
   `getmempooldescendants` and  `getmempoolentry` when verbosity is set to
   `true` with sub-fields `ancestor`, `base`, `modified` and `descendant`
   denominated in BCH. This new field deprecates previous fee fields, such a
   `fee`, `modifiedfee`, `ancestorfee` and `descendantfee`.


Dynamic creation of wallets
---------------------------------------
  - Previously, wallets could only be loaded or created at startup, by
    specifying `-wallet` parameters on the command line or in the bitcoin.conf
    file. It is now possible to create wallets dynamically at runtime:

  - New wallets can be created (and loaded) by calling the `createwallet` RPC.
    The provided name must not match a wallet file in the `walletdir` directory
    or the name of a wallet that is currently loaded.

  - This feature is currently only available through the RPC interface.

 - Wallets loaded dynamically through the RPC interface may now be displayed in
   the Devault-Core GUI.
 - The default wallet will now be labeled `[default wallet]` in the DeVault-Core
   GUI if no name is provided by the `-wallet` option on start up.
 - It is now possible to unload wallets dynamically at runtime. This feature is
   currently only available through the RPC interface.
 - Wallets dynamically unloaded will now be reflected in the gui. Also the
   unloadwallet RPC is synchronous, meaning that it blocks until the
   wallet is fully unloaded.
 - The RPC `createwallet` now has an optional `blank` argument that can be used
   to create a blank wallet. Blank wallets do not have any keys or HD seed.
   They cannot be opened in software that is version 1.1.4 or older


