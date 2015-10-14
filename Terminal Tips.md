## Find a Core Data error number
```
# $ cd /System/Library/Frameworks
$ cd /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/
$ grep -RFw '134130' $(find . -name "*Errors.h" )
=> ./CoreData.framework/Versions/A/Headers/CoreDataErrors.h:    NSMigrationMissingSourceModelError               = 134130, // migration failed due to missing source data model
```

## Generate .strings file
    $ find ./ -name "*.m" -print0 | xargs -0 genstrings -o en.lproj

## Find the pull request where a commit was merged
    $ git log --merges --ancestry-path --oneline <SHA>..origin | tail

## List simulator devices
    $ xcrun simctl list devices

## Simulator location
    $ cd ~/Library/Developer/CoreSimulator

## Crash Reports

[Understanding and Analyzing iOS Application Crash Reports](https://developer.apple.com/library/ios/technotes/tn2151/_index.html)