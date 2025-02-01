---
title: Tworzenie Pluginu
description: 
published: 1
date: 2025-01-26T17:33:54.518Z
tags: 
editor: markdown
dateCreated: 2025-01-26T09:51:41.504Z
---

# Drzewo Plików i Katalogów

Typy plików:

- FILETYPE 
1.   network
1.   storage
1.   services
1.   usermgmt
1.   diagnostics

```shell

├── DEBIAN
│   ├── changelog
│   ├── compat
│   ├── control
│   ├── copyright
│   ├── install
│   ├── postinst
│   ├── postrm
│   ├── rules
│   └── triggers
└── usr
    ├── sbin
    │   └── plugin-file-name
    └── share
        └── openmediavault
            ├── confdb
            │   └── create.d
            │       └── conf.system.network.PLUGINNAME.sh
            ├── datamodels
            │   └── conf.system.network.PLUGINNAME.json
            ├── engined
            │   ├── inc
            │   │   └── PLUGINNAME.inc  # LogFileSpec
            │   ├── module
            │   │   └── PLUGINNAME.inc
            │   └── rpc
            │       └── PLUGINNAME.inc
            ├── locale
            │   ├── openmediavault-PLUGINNAME.pot
            │   ├── pl
            │   │   └── openmediavault-PLUGINNAME.po
            │   └── pl_PL
            │       └── openmediavault-PLUGINNAME.po
            └── workbench
                ├── component.d
                │   ├── omv-network-PLUGINNAME-form-page.yaml
                │   ├── omv-network-PLUGINNAME-navigation-page.yaml
                │   └── omv-network-PLUGINNAME-noip-form-page.yaml
                ├── log.d
                │   └── PLUGINNAME.yaml
                ├── navigation.d
                │   └── network.PLUGINNAME.yaml
                └── route.d
                    └── network.PLUGINNAME.yaml


```

# Pliki

### rpc

 `` PLUGINNAME.inc ``
 
```php 
<?php

#SET NAME filetypePluginame example - ServicesExample
class ServicesExample extends \OMV\Rpc\ServiceAbstract {

  #SET NAME filetypePluginame example - ServicesExample
	public function getName() {
		return "NAME";
	}
  
  
  #Register Method to use function
	public function initialize() {
        $this->registerMethod('getSettings');
        $this->registerMethod('setSettings');
	}
}
?>
```

### debian

``changelog``
``control`` - Set name and author plugin
``postinst`` - Tworzenie bazdy danych, katalogów, oraz instalowanie potrzebnych bibliotek jakich potrzebujesz
``postrm`` - Kod używany podczas odinstalowywania pluginu

### workbench

# Datatable

# Form

# Baza Danych zapis oraz odczyt

# Pliki wykonywalne bash

# Generowanie pliku deb oraz instalacja

```shell
cd openmediavault-pluginame
dpkg-buildpackage -us -uc
```

``Install``

```shell
dpkg -i openmediavault-pluginname_VERSION_all.deb
```