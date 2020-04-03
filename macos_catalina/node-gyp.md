# Fix `node-gyp` Compile Errors

node-gyp requres Xcode Command Line Tools to compile node-gyp
Xcode is not being installed in a way that node-gyb can use.

I noticed this error after running an `npm i` on one of our newer projects after upgrading to a new macboook running Catallina:
```bash
> node-gyp rebuild

No receipt for 'com.apple.pkg.CLTools_Executables' found at '/'.

No receipt for 'com.apple.pkg.DeveloperToolsCLILeo' found at '/'.

No receipt for 'com.apple.pkg.DeveloperToolsCLI' found at '/'.

gyp: No Xcode or CLT version detected!
gyp ERR! configure error
gyp ERR! stack Error: `gyp` failed with exit code: 1
gyp ERR! stack     at ChildProcess.onCpExit (/Users/wdzajicek/.nvm/versions/node/v12.16.1/lib/node_modules/npm/node_modules/node-gyp/lib/configure.js:351:16)
gyp ERR! stack     at ChildProcess.emit (events.js:311:20)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:275:12)
gyp ERR! System Darwin 19.4.0
gyp ERR! command "/Users/wdzajicek/.nvm/versions/node/v12.16.1/bin/node" "/Users/wdzajicek/.nvm/versions/node/v12.16.1/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "rebuild"
gyp ERR! cwd /Users/wdzajicek/repositories/tuition-and-aid/node_modules/fsevents
gyp ERR! node -v v12.16.1
gyp ERR! node-gyp -v v5.0.5
gyp ERR! not ok
```

After doing some research I found that bash wasnt seeing my Xcode installation.

Run the following commands to check your Xcode CLT's installation:

The following command returned nothing:
```bash
/usr/sbin/pkgutil --packages | grep CL
```

```bash
/usr/sbin/pkgutil --pkg-info com.apple.pkg.CLTools_Executables
# No receipt for 'com.apple.pkg.CLTools_Executables' found at '/'
```

## Test your Xcode installation:

1. `/usr/sbin/pkgutil --packages | grep CL`
  - `com.apple.pkg.CLTools_Executables` should be listed. If it isn't, this test failed.
2. `/usr/sbin/pkgutil --pkg-info com.apple.pkg.CLTools_Executables`
  - `version: 11.0.0` (or later) should be listed. If it isn't, this test failed.

## The solution

Xcode was one of the first things I installed. However, running the commands above resulted in failing tests.
If I ran `xcode-select --install` it would return: ` xcode-select: error: command line tools are already installed, use "Software Update" to install updates`

Instead, I had to manually download `Command_Line_Tools_for_Xcode_11.4.dmg` from <developer.apple.com>.
Running the installer fixed my xcode installation.
