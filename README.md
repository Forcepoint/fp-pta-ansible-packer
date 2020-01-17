# packer

Setup a system for running Packer.

## Requirements

None

## Role Variables

### REQUIRED

None

### OPTIONAL

* packer_version: The version of Packer to install.
* packer_checksum: The checksum for the Packer binaries.
* packer_download_url: The website to download the Packer executable from. 
  Useful if you need to access the Hashicorp site through a proxy like Artifactory.
* packer_vsphere_iso_url: The url to download the vsphere-iso plugin, if you want that available. 
  At the time of this writing, it is said that the vsphere-iso plugin code is going to be merged
  into the Packer code base, so in the future the plugin will not require a separate install. For now,
  the file is hosted in Amazon S3 by default, which is crazy slow to download. 
  I've found hosting the file in a local Artifactory repository yields much faster downloads.

## Dependencies

None

## Example Playbook

    - hosts: servers
      vars:
        packer_version: 1.2.5
        packer_checksum: sha256:bc58aa3f3db380b76776e35f69662b49f3cf15cf80420fc81a15ce971430824c
        packer_download_url: https://artifactory.COMPANY.com/artifactory/releases.hashicorp.com
        packer_vsphere_iso_url: https://artifactory.COMPANY.com/artifactory/software/Hashicorp/Packer/jetbrains-infra/2.3/packer-builder-vsphere-iso.linux
      roles:
      - role: packer

## License

BSD

## Author Information

Jeremy Cornett <jeremy.cornett@forcepoint.com>
