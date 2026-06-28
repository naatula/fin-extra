# Finner

Finner is designed to be an enhanced Finnish keyboard layout. The keylayout was
designed to be very easy to learn and it keeps changes to the standard Finnish
layout as minimal as possible, while providing much better usability. The main
benefit over the standard Finnish layout is the minimized usage of Option (or
AltGr) and not needing to use dead keys when typing ASCII characters, and the
main benefit over the US layout is easy access to the very commonly used `Ä`
and `Ö`.

The repository contains the macOS `.keylayout` file, the Windows `.klc` file,
and the Linux XKB `finner` symbols file.

## macOS installation

1. Move or symlink `Finner.keylayout` into `/Library/Keyboard Layouts/`
2. Log out and log back in
3. Select the new keyboard layout from System Settings

(You will see this warning message about the 'Installed Input Source', but, as
you can [and should] verify from the plaintext `.keylayout` file, there is
absolutely no executable code in it which could do something like this.)
![Unwarranted warning in macOS settings](./images/mac_settings.png)

## Linux installation

Tested on Ubuntu 24.04 LTS (GNOME on Wayland). The layout is packaged as an
XKB variant of the Finnish (`fi`) layout and works on both Wayland and Xorg.

### Quick install (recommended)

```
curl -fsSL https://raw.githubusercontent.com/naatula/finner/master/install-linux.sh | sudo bash
```

Then log out and log back in, and add **Finnish (Finner)** from
**Settings → Keyboard → Input Sources**.

### Manual install

1. Install the symbols file:
   ```
   sudo cp finner /usr/share/X11/xkb/symbols/finner
   ```

2. Register it as a variant of `fi` so it shows up in system settings. Append
   the following line inside the `fi` layout's `<variantList>` element in
   `/usr/share/X11/xkb/rules/evdev.xml`:
   ```xml
   <variant>
     <configItem>
       <name>finner</name>
       <description>Finnish (Finner)</description>
     </configItem>
   </variant>
   ```
   And append this line to the `! variant` section of
   `/usr/share/X11/xkb/rules/evdev.lst`:
   ```
     finner          fi: Finnish (Finner)
   ```

3. Log out and log back in.

4. Open **Settings → Keyboard → Input Sources**, click **+**, and select
   **Finnish → Finnish (Finner)**.

To try it out in the current X session without installing system-wide:
```
setxkbmap -layout fi -variant finner
```

## Windows installation

1. Download [Microsoft Keyboard Layout Creator](https://www.microsoft.com/en-us/download/details.aspx?id=102134) and open it
2. From 'File' > 'Load Source File...' open the `Finner.klc` file
3. From 'Project' > select 'Build DLL and Setup package', ignore the verification warnings
4. Run the `setup.exe` file from the location it got created to
5. Select the new keyboard layout from Windows Settings

## All symbols from all layers

### No modifiers

```
`1234567890+\
qwertyuiop[]
asdfghjklöä'
<zxcvbnm,.-
```
(Pressing space types ` `, the normal `U+0020 SPACE (SP)` character)

### Shift

```
~!"#^%&/()=?|
QWERTYUIOP{}
ASDFGHJKLÖÄ*
>ZXCVBNM;:_
```
(Pressing space types ` `, the normal `U+0020 SPACE (SP)` character)

### Option (AltGr on Windows)

```
´¡@£$€¼½¾≠≈¿¬
¤¥€®™☐ü↑Ωπå”
√∑∆☒☑↔←↓→œæ’
≤«‹©∫§№µ<>–
```
(Pressing space doesn't type anything, to avoid mistakenly entering non-standard whitespace)

### Option + Shift (AltGr + Shift on Windows)

```
°¹²³⁴⁵⁶⁷⁸⁹⁰±¦
⋅×÷‰†¨Ü⇑↳¶Å”
 ß ′″⇔⇐⇓⇒ŒÆ’
≥»›^ • …≤≥—
```
(Pressing space types ` `, the `U+00A0 NO-BREAK SPACE (NBSP)` character)
