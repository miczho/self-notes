## Browser Setup

*THIS ARTICLE CONTAINS DETAILS ABOUT MY PERSONAL BROWSER ENVIRONMENT SETUP*


| Table of Contents |
| ----------------- |
| [Extensions](#extensions) |
| [Firefox](#firefox) |
| [Ungoogled Chromium](#ungoogled_chromium) |


# Extensions <a id="extensions"></a>

Extensions that I use across browsers:

<table>
    <tr>
        <td></td>
        <th><i>DESCRIPTION</i></th>
        <th>Firefox</th>
        <th>Ungoogled<br>Chromium</th>
    </tr>
    <tr>
        <th>Bitwarden</th>
        <td>password manager</td>
        <td><a href="https://addons.mozilla.org/en-US/firefox/addon/bitwarden-password-manager/">link</a></td>
        <td><a href="https://chromewebstore.google.com/detail/bitwarden-password-manage/nngceckbapebfimnlniiiahkandclblb">link</a></td>
    </tr>
    <tr>
        <th>Raindrop.io</th>
        <td>bookmarks manager</td>
        <td><a href="https://addons.mozilla.org/en-US/firefox/addon/raindropio/">link</a></td>
        <td><a href="https://chromewebstore.google.com/detail/raindropio/ldgfbffkinooeloadekpmfoklnobpien">link</a></td>
    </tr>
    <tr>
        <th>uBlock Origin</th>
        <td>ad blocker</td>
        <td><a href="https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/">link</a></td>
        <td><a href="https://chromewebstore.google.com/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm">link</a></td>
    </tr>
    <tr>
        <th>SingleFile</th>
        <td>save a page into<br>a single HTML file</td>
        <td><a href="https://addons.mozilla.org/en-US/firefox/addon/single-file/">link</a></td>
        <td><a href="https://chromewebstore.google.com/detail/singlefile/mpiodijhokgodhhofbcjdecpffjipkle">link</a></td>
    </tr>
    <tr>
        <th>Simplify Copilot</th>
        <td>autofill job apps</td>
        <td><a href="https://addons.mozilla.org/en-US/firefox/addon/simplify-jobs/">link</a></td>
        <td><a href="https://chromewebstore.google.com/detail/simplify-copilot-autofill/pbanhockgagggenencehbnadejlgchfc">link</a></td>
    </tr>
    <tr>
        <th>Chromium<br>Web Store</th>
        <td>install & update Chrome<br>extensions privately</td>
        <td>N/A</td>
        <td><a href="https://github.com/NeverDecaf/chromium-web-store">link</a></td>
    </tr>
</table>


# Firefox <a id="firefox"></a>

[Flatpak install](https://flathub.org/apps/org.mozilla.firefox) on Flathub:

```shell
flatpak install flathub org.mozilla.firefox
```

Firefox may sometimes stutter during video playback.  
On Linux, the Flatpak version will come with video codecs, but the local package version may not.


# Ungoogled Chromium <a id="ungoogled_chromium"></a>

[Download instructions](https://github.com/ungoogled-software/ungoogled-chromium?tab=readme-ov-file#downloads) found on GitHub.

Enabling Google in search bar:

1. Go to `chrome://settings/searchEngines`

2. Scroll to `Site search` and click `Add`

3. Fill and save form like so:
    - Name -- `Google`
    - Shortcut --`google.com`
    - URL -- `https://www.google.com/search?q=%s`
    - Suggestions URL -- `https://www.google.com/complete/search?client=chrome&q=%s`

4. Click the triple dot menu near `Google` and select `Make default`

5. Go to `chrome://settings/syncSetup`

6. Enable `Improve search suggestions`