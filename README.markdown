## CocoaLibSpotify

This repository forks the official [cocoalibspotify](https://github.com/spotify/cocoalibspotify), in order to add support for sending `Float32`'s to the iOS hardware.

Major differences between this and the official cocoalibspotify:

- `SPCoreAudioController` now has support for an arbitrary `AURenderCallbackStruct` to be passed all `Float32`'s before they are sent to the RemoteIO unit (for potential modification).
- no control over volume on an internal AUMixer unit (was removed for incompatability with necessary AUGraph modifications, and because iOS apps can control system volume directly).
- This fork also removes the use of Objective-C categories in cocoalibspotify, which necessitated the use of the `-all_load` and `-ObjC` linker flags. Those are no longer necessary.

Caveat Emptor
- probably has some gnarly bugs, & probably doesn't pass any tests.
- only tested with iOS

Future possibility: rework the internals of the `SPCoreAudioController` in order to allow a subclass of the selfsame to accomplish what I've done here by editing SPCoreAudioController.m directly; i.e. make `Float32` support optional rather than mandatory.
