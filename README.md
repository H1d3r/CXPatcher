 <img width="100" height="100" alt="CXPatcher Logo" src="https://github.com/italomandara/CXPatcher/raw/main/pacher%20icon.png">

# CXPatcher

A patcher to upgrade CrossOver dependencies and improve compatibility

Discord: https://discord.com/channels/793156450821865513/1121334417344974929

This is an **unofficial patcher** for CrossOver and CodeWeavers is not - by any
means - involved in this or has anything to do with this app, and although has
been tested, this software may render the app unusable or unstable,
**USE AT YOUR OWN RISK**, this also will void any official support from
CodeWeavers, If you still need support from CodeWeavers, download the original
unmodified app and please don't report problems to them after your app is
patched.

If you have any issues after your app has been patched you can download a new
copy of CrossOver.

For more info: [https://www.codeweavers.com/support/forums/general/?t=27;msg=257865](https://www.codeweavers.com/support/forums/general/?t=27;msg=257865)

## What version of CrossOver does it support?

CXPatcher up to 0.3 will support only 22.x.x
CXPatcher from 0.4 on will support 23.x.x
CXPatcher from 0.5 on will support 24.x.x
CXPatcher from 0.6 on will support 25.x.x 
(keep an eye on the specific verson)

## What MacOS does it support

Ventura (13) or newer
Currently GPTK requires MacOS Sonoma

## What does it do?

This patcher will upgrade your CrossOver app with the latest DXVK and MoltenVK
patched for improved compatibility, and dramatically extends compatibility with
Unreal engine 4 games.

## What does it NOT do?

- Games with anti-cheat or anti-tamper will not work

- ~DX12 games will not work unless playable via the popular -dx11 option~
DX12 games will now work via GPTK

## Instructions

You need to have an unmodified version of CrossOver, you can download it at:
[https://www.codeweavers.com/account/downloads](https://www.codeweavers.com/account/downloads).
Please make sure the app has been registered or ran at least once, to make sure
the latest DXVK is activated properly. You may need to switch off
DXVK and on again, if you don't you will need to re-download it. If the
patcher renders the app unusable you can either use the restore function (see
instructions below) or download it again from the website, it doesn't do any
permanent modifications to your 'bottles'.

## Installation

### Direct Download

You can download the latest version directly from the [Release Page](https://github.com/italomandara/CXPatcher/releases).

### Homebrew

Alternatively, you may use Homebrew. See the
[homebrew-CXPatcher repo](https://github.com/italomandara/homebrew-CXPatcher)
for detailed instructions.

## New Bottle path

CXPatcher will override the default bottle path to have its own folder prefixed with 'CXP' in the same one that contains the 'Bottles' folder.
That's because lots of users keep having trouble when using old bottles created with the original Crossover.
This way you'll be forced to create a new bottle just for the Patched Crossover so that you'll no longer have this kind of issue.

If you don't like that you can disable it, it's enabled by default as you can see in the picture below:

<img width="452" alt="Screenshot 2023-09-24 at 18 09 09" src="https://github.com/italomandara/CXPatcher/assets/12135454/b421b96e-5951-48e9-a333-42977021ca54">


## Patching with gptk

There are new upcoming technologies developed this year that are capable of
running DirectX 12 games and now you can have those embedded in CrossOver!
In order to integrate that in CrossOver you just need switch on "Integrate D3DMetal (GPTK)"

<img width="300" alt="integrate external resources" src="https://github.com/italomandara/CXPatcher/assets/12135454/0da08a95-5003-46c1-985c-80f2ff6dd256">
<img width="401" alt="integrate external resources" src="https://github.com/italomandara/CXPatcher/assets/12135454/9f709365-cd25-4d34-a737-6f68ff2bb491">

- now you can patch CrossOver as usual via either drag'n'drop or file selector
(click in the drop area)
- enjoy your DX12 games!

## Restoring a patched app to the original app

Maybe you changed your mind and prefer to use your original CrossOver app.
You can restore by going to the `file -> restore menu`

<img width="168" alt="restore" src="https://github.com/italomandara/CXPatcher/assets/12135454/81a09c09-4209-4af1-911b-461efcaf2421">


## Upgrade from an old patch

If you patched from an old version and you just want to update the patched
CrossOver app just turn on the option and drag 'n drop

<img width="399" alt="repatch" src="https://github.com/italomandara/CXPatcher/assets/12135454/8f8295ed-5da3-4a5f-93c0-4daa4851b0ec">

## Troubleshoting

**If your env vars doesn't work anymore or can't enable/disable fast math**:
use the env variable `CXPATCHER_SKIP_NTDLLHACKS=1` and then any env var should
work as usual
**For other issues**:
try: `NAS_DISABLE_UE4_HACK=1`

## Color profiles for UE4 games

You can change the way the colors are processed in UE4 games.

### Examples

#### disable color profiles

(old greyish colors but may improve performance or fix dark or oversaturated colors)

`NAS_TONEMAP_C=0`

#### Color profile for Stray

`NAS_TONEMAP_C=clamp({inputColor} * float3x3( 0.2126 + 0.7874 * 1.5, 0.7152 -
0.7152 * 1.5, 0.0722 - 0.0722 * 1.5, 0.2126 - 0.2126 * 1.5, 0.7152 + 0.2848 *
1.5, 0.0722 - 0.0722 * 1.5, 0.2126 - 0.2126 * 1.5, 0.7152 - 0.7152 * 1.5,
0.0722 + 0.9278 * 1.5 ) * 2 - float3(0.28, 0.2, 0.16), 0.0, 1.0)`

`NAS_TONEMAP_C` uses standard MSL shading language, as long as it's done in one
line, you can use {inputColor} as a variable and modify the colors, or give any
effect you like using matrix transforms, WARNING: do not copy paste any code
from unknown sources, and do this only if you know what you're doing, otherwise,
have fun!

**Note:** you may need to use `CXPATCHER_SKIP_DXVK_ENV=1` to override built in
settings for games that already have a profile `NAS_TONEMAP_C`, also only works
for UE4 games.

## Credits

Many thanks to the developers behind DXVK and MoltenVK patches:

- @gcenx [https://github.com/Gcenx](https://github.com/Gcenx)
- @nastys [https://github.com/nastys](https://github.com/nastys)

thanks for the great help and for providing the latest binaries.
