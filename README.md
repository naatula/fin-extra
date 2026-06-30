# FIN Extra

FIN Extra is a cross-platform Finnish keyboard layout with improvements for
developers and power users.

The repository contains the macOS `FIN Extra.keylayout` file, the Windows
`FIN Extra.klc` file, and the Linux XKB `fin_extra` symbols file.

## Symbols

### No modifiers

```
`1234567890+\
qwertyuiop[]
asdfghjklöä'
<zxcvbnm,.-
```

### Shift

```
~!"#^%&/()=?|
QWERTYUIOP{}
ASDFGHJKLÖÄ*
>ZXCVBNM;:_
```

### Option (AltGr on Windows)

```
´¡@£$€¼½¾≠≈¿¬
¤¥€®™☐ü↑Ωπå"
√∑∆☒☑↔←↓→œæ'
≤«‹©∫§№µ<>–
```
(Pressing space doesn't type anything, to avoid mistakenly entering non-standard whitespace)

### Option + Shift (AltGr + Shift on Windows)

```
°¹²³⁴⁵⁶⁷⁸⁹⁰±¦
⋅×÷‰† Ü⇑↳¶Å"
 ß ′″⇔⇐⇓⇒ŒÆ'
≥»›  • …≤≥—
```
(Pressing space types ` `, the `U+00A0 NO-BREAK SPACE (NBSP)` character)

## Linux installation

Tested on Ubuntu 24.04 LTS (GNOME on Wayland). The layout is packaged as an
XKB variant of the Finnish (`fi`) layout and works on both Wayland and Xorg.

### Quick install (recommended)

```
curl -fsSL https://raw.githubusercontent.com/naatula/finner/master/install-linux.sh | sudo bash
```

Then log out and log back in, and add **Finnish (FIN Extra)** from
**Settings → Keyboard → Input Sources**.

### Manual install

1. Install the symbols file:
   ```
   sudo cp fin_extra /usr/share/X11/xkb/symbols/fin_extra
   ```

2. Register it as a variant of `fi` so it shows up in system settings. Append
   the following line inside the `fi` layout's `<variantList>` element in
   `/usr/share/X11/xkb/rules/evdev.xml`:
   ```xml
   <variant>
     <configItem>
       <name>fin_extra</name>
       <description>Finnish (FIN Extra)</description>
     </configItem>
   </variant>
   ```
   And append this line to the `! variant` section of
   `/usr/share/X11/xkb/rules/evdev.lst`:
   ```
     fin_extra       fi: Finnish (FIN Extra)
   ```

3. Log out and log back in.

4. Open **Settings → Keyboard → Input Sources**, click **+**, and select
   **Finnish → Finnish (FIN Extra)**.

To try it out in the current X session without installing system-wide:
```
setxkbmap -layout fi -variant fin_extra
```

## Windows installation

### Quick install (recommended)

1. Download and extract the [pre-built setup zip](./finextra.zip)
2. Run the `setup.exe` file

### Build and install the layout from source

1. Download [Microsoft Keyboard Layout Creator](https://www.microsoft.com/en-us/download/details.aspx?id=102134) and open it
2. From 'File' > 'Load Source File...' open the `FIN Extra.klc` file
3. From 'Project' > select 'Build DLL and Setup package', ignore the verification warnings
4. Run the `setup.exe` file from the location it got created to
5. Select the new keyboard layout from Windows Settings

## macOS installation

1. Move or symlink `FIN Extra.keylayout` into `/Library/Keyboard Layouts/`
2. Log out and log back in
3. Select the new keyboard layout from System Settings
