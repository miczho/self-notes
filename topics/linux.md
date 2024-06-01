### Linux & Its Distributions

*This article discusses what Linux is and the differences between each distro*

| Section | Title |
| ------- | ----- |
| 01 | [Package Management](#01) |
| 02 | [Release Cycles](#02) |

<a id="01"></a>
# Package Management

apt, rpm (dnf, yum), pacman, flatpak

<a id="02"></a>
# Release Cycles

Table of the 3 major types of release cycles:

<table>
    <tr>
        <td></td>
        <th>Stable/LTS</th>
        <th>Fixed</th>
        <th>Rolling</th>
    </tr>
    <tr>
        <th>Typical Lifespan</th>
        <td>several years</td>
        <td>6 months - 1 year</td>
        <td>1 day</td>
    </tr>
    <tr>
        <th>Update Frequency</th>
        <td>infrequent</td>
        <td>frequent</td>
        <td>very frequent</td>
    </tr>
    <tr>
        <th>Minor Updates</th>
        <td>
            bug fixes,<br>
            security
        </td>
        <td>
            new core components,<br>
            bug fixes,<br>
            security
        </td>
        <td>
            new features,<br>
            new core components,<br>
            bug fixes,<br>
            security
        </td>
    </tr>
    <tr>
        <th>Release Updates</th>
        <td>
            new features,<br>
            new core components
        </td>
        <td>
            new features
        </td>
        <td></td>
    </tr>
    <tr>
        <th>Suitable For</th>
        <td>production environments</td>
        <td>daily users</td>
        <td>hobbyists</td>
    </tr>
</table>

Stable release distros:
- Debian
- Ubuntu LTS
- Red Hat Enterprise Linux (RHEL) - [release timeline](../img/rhel_release.png)

Fixed release distros:
- Ubuntu - [release timeline](../img/ubuntu_release.png)
- Fedora - [release timeline](../img/fedora_release.png)

Rolling release distros:
- Arch Linux - no release timeline bc versioning doesn't exist
