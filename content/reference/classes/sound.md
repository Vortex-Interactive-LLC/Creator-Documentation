---
title: Sound
description: Plays an uploaded audio asset, globally or from a position in the world.
---

## Summary

A `Sound` plays an audio asset you uploaded on the creator dashboard. Parent it to a `Part` and it plays from that part's position, getting quieter with distance. Parent it anywhere else, such as `Workspace` or a `Folder`, and every player hears it at the same volume.

You can use a sound while it is still under review, but a game can only be published once every sound in it is approved.

### Example

```luau
local sound = Instance.new("Sound")
sound.SoundId = 1234
sound.Volume = 0.8
sound.Looped = true
sound.Parent = workspace.Speaker

sound.Loaded:Wait()
print("length:", sound.TimeLength)
sound:Play()

sound.Ended:Connect(function()
    print("done")
end)
```

## Properties

- `SoundId` - `number`, the id of the sound asset. A string such as `"vortex://1234"` is also accepted. Defaults to `0`, which plays nothing;
- `Volume` - `number` from `0` to `10`. Defaults to `0.5`;
- `PlaybackSpeed` - `number` from `0.01` to `20`. Defaults to `1`;
- `Looped` - `boolean`, whether the sound starts again when it reaches the end. Defaults to `false`;
- `Playing` - `boolean`, whether the sound is playing. Setting it to `true` resumes it, and `false` pauses it. Defaults to `false`;
- `IsPlaying` - `boolean`, the same as `Playing`;
- `TimePosition` - `number`, the playback position in seconds. Reading it gives the current position. Setting it jumps to that position;
- `TimeLength` - `number`, the length of the sound in seconds. Read-only. It is `0` until the sound is loaded;
- `IsLoaded` - `boolean`, whether the length of the sound is known. Read-only;
- `RollOffMinDistance` - `number`, the distance in studs within which a positional sound plays at full volume. Defaults to `10`;
- `RollOffMaxDistance` - `number`, the distance in studs beyond which a positional sound is silent. Defaults to `10000`;
- `Name` - the name of the instance;
- `ClassName` - `"Sound"`;
- `Parent` - the instance it is parented to.

Values outside the allowed range are clamped. `Changed` and `GetPropertyChangedSignal` do not fire for these properties.

## Methods

- `Play()` - starts the sound from the beginning, even if it is already playing;
- `Pause()` - pauses the sound where it is;
- `Resume()` - continues a paused sound;
- `Stop()` - stops the sound and returns to the beginning.

## Signals

All signals support `Connect`, `Once`, and `Wait`, and fire in both server and client scripts.

- `Loaded` - the length of the sound became known;
- `Played` - the sound started from the beginning;
- `Paused` - the sound was paused;
- `Resumed` - a paused sound continued;
- `Stopped` - the sound was stopped;
- `Ended` - a sound that is not looped reached its end. `Playing` is set back to `false`.

## Uploading sounds

Upload audio on the Sounds page of the creator dashboard. MP3, WAV, OGG, FLAC, and M4A files up to 20 MB and 5 minutes are accepted. Every upload costs Volts based on its length, and the Volts are not refunded if the sound is deleted. Uploads are reviewed before they are approved for everyone. See also [`ContentProvider`](./content-provider.md).
