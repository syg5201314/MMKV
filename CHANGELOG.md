# MMKV Change Log

## v1.0.13 / 2018-11-09
### iOS / macOS
What's new  

* Special chars like `/` are supported in MMKV now. The file name of MMKV with special mmapID will be encoded with md5 and stored in seperate folder.
* Add **callback** for MMKV error handling. You can make MMKV to recover instead of discard when crc32 check fail happens.
* Add `trim` and `close` operation. Generally speaking they are not necessary in daily usage. Use them if you worry about disk / memory / fd usage.
* Fix an issue that MMKV's file size might expand unexpectly large in some case.

Known Issues

* Setting `nil` value to reset a key will be ignored. Use `remove` instead.

### Android
What's new  

* Add static linked of libc++ to trim AAR size. Use it when there's no other lib in your App embeds `libc++_shared.so`. Or if you already have an older version of `libc++_shared.so` that doesn't agree with MMKV.  
Add `implementation 'com.tencent:mmkv-static:1.0.13'` to your App's gradle setting to integrate.
* Special chars like `/` are supported in MMKV now. The file name of MMKV with special mmapID will be encoded with md5 and stored in seperate folder.
* Add **callback** for MMKV error handling. You can make MMKV to recover instead of discard when crc32 check fail happens.
* Add `trim` and `close` operation. Generally speaking they are not necessary in daily usage. Use them if you worry about disk / memory / fd usage.
* Fix an issue that MMKV's file size might expand unexpectly large in some case.

Known Issues

* Setting `null` value to reset a key will be ignored. Use `remove` instead.

## v1.0.12 / 2018-10-18
### iOS / macOS
What's new  

* Fix `mlock` fail on some devices
* Fix a performance issue caused by mistakenly merge of test code
* Fix CocoaPods integration error of **macOS**

### Android / 2018-10-24
What's new  

* Fix `remove()` causing data inconsistency on `MULTI_PROCESS_MODE`


## v1.0.11 / 2018-10-12
### iOS / macOS
What's new  

* Port to **macOS**
* Support **NSCoding**  
You can  store NSArray/NSDictionary or any object what implements `<NSCoding>` protocol.
* Redesign Swift interface
* Some performance improvement

Known Issues

* MMKV use mmapID as its filename, so don't contain any `/` inside mmapID.
* Storing a value of `type A` and getting by `type B` may not work. MMKV does type erasure while storing values. That means it's hard for MMKV to do value-type-checking, if not impossible.

### Android 
What's new  

* Some performance improvement

Known Issues

* Getting a MMKV instance with mmapID that contains `/` may fail.  
MMKV uses mmapID as its filename, so don't contain any `/` inside mmapID.
* Storing a value of `type A` and getting by `type B` may not work.  
MMKV does type erasure while storing values. That means it's hard for MMKV to do value-type-checking, if not impossible.
* `registerOnSharedPreferenceChangeListener` not supported.  
This is intended. We believe doing data-change-listener inside a storage framework smells really bad to us. We suggest using something like event-bus to notify any interesting clients.

## v1.0.10 / 2018-09-21  

 * Initial Release
