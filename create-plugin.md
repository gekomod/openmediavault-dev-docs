---
title: Create Plugin
description: 
published: 1
date: 2025-02-01T07:03:21.088Z
tags: 
editor: markdown
dateCreated: 2025-01-26T17:35:57.754Z
---

# Tree files and directory

Type Files:

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

# Database

### Tabset {.tabset}

#### conf.service.example

```bash
#!/bin/sh

set -e

. /usr/share/openmediavault/scripts/helper-functions

SERVICE_XPATH_NAME="PLUGINNAME"
SERVICE_XPATH="/config/services/${SERVICE_XPATH_NAME}"

if ! omv_config_exists "${SERVICE_XPATH}"; then
    omv_config_add_node "/config/services" "${SERVICE_XPATH_NAME}"
    omv_config_add_key "${SERVICE_XPATH}" "enable" "0"
    omv_config_add_key "${SERVICE_XPATH}" "ADD_NEXT_KEY" "true" # Option true,false or everyone else
fi

exit 0
```
**Notes**:
- The file should be created in the directory /usr/share/openmediavault/confdb/create.d/conf.service.example.sh

#### conf.service.example.json

```json
{
	"type": "config",
	"id": "conf.service.PLUGINNAME",
	"title": "PLUGINNAME",
	"queryinfo": {
		"xpath": "//services/PLUGINNAME",
		"iterable": false
	},
	"properties": {
		"enable": {
			"type": "boolean",
			"default": false
		},
		"ADD_NEXT_KEY": {
			"type": "boolean",
			"default": true
		}
	}
}
```
**Notes**:
- The file should be created in the directory /usr/share/openmediavault/datamodels/conf.service.example.json

#### Usage in RPC file

```php
// Is service enabled?
                $db = \OMV\Config\Database::getInstance();
                $object = $db->get("conf.service.PLUGINNAME");
                if (FALSE === $object->get("enable")) {
                        $result = gettext("Service disabled");
                } else {
                        $result = gettext("Service enabled");
                }
```

#### GetSettings in RPC

```php
	function getSettings($params, $context) {
        $this->validateMethodContext($context, [ 'role' => OMV_ROLE_ADMINISTRATOR ]);
        $db = \OMV\Config\Database::getInstance();
        $object = $db->get('conf.system.FILETYPE.PLUGINNAME');
        return $object->getAssoc();
	}
```

#### SetSettings in RPC

```php
	function setSettings($params, $context) {
        $this->validateMethodContext($context, ['role' => OMV_ROLE_ADMINISTRATOR]);
        $db = \OMV\Config\Database::getInstance();
        $object = $db->get('conf.system.FILETYPE.PLUGINNAME');
        $object->setAssoc($params);
        $db->set($object);
    
        return $object->getAssoc();
	}
```

# Files

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
``postinst`` - Creating a database, directories, and installing the necessary libraries you need
``postrm`` - Code used when uninstalling a plugin

### workbench

# Datatable

# Form

```yaml
version: "1.0"
type: component
data:
  name: omv-FILETYPE-PLUGINNAME-form-page
  type: formPage
  config:
    request:
      service: NetworkDnshost  #FILETYPE PLUGINNAME
      get:
        method: getSettings # From RPC file
      post:
        method: setSettings # From RPC file
    fields:
      - type: checkbox
        name: option1_fromDB
        label: _("NAME OPTION1")
        value: false
      - type: textInput
        name: option2_fromDB
        label: _("Option Name2")
        value: "username"
    buttons:
      - template: submit
      - template: cancel
        execute:
          type: url
          url: "/FILETYPE/PLUGINNAME"
```

# Bash executables
In RPC file command example

```php
    function Example($params) {
        return $this->execBgProc(function($bgStatusFilename, $bgOutputFilename)
		  use ($object, $params) {
        $db = \OMV\Config\Database::getInstance();
        $provider = $params['provider'];
        $object = $db->get('conf.system.FILETYPE.PLUGINNAME');
        if (FALSE === $object->get("".$provider."") ) {
              throw new \OMV\Exception(
				"Failed to run scheduled job because the service is disabled.");
        } else {
            $cmdArgs = [];
			$cmdArgs[] = "--shell";
			$cmdArgs[] = "--non-interactive";
			$cmdArgs[] = "--";
			$cmdArgs[] = build_path(DIRECTORY_SEPARATOR, \OMV\Environment::get("OMV_CRONSCRIPTS_DIR"), sprintf("$provider-%s", 100));

             $cmd = new \OMV\System\Process("python3 /usr/sbin/EXAMPLE.py", "-d $provider");
             $cmd->setRedirect2to1();
             $cmd->execute($output);
             $cmdLine = $cmd->getCommandLine();
             $stats = implode("\n", $output);
            
             $exitStatus = $this->exec($cmdLine, $output, $bgOutputFilename);
             
             if (0 !== $exitStatus)
				throw new \OMV\ExecException($cmdLine, $output, $exitStatus);
            
            return $output;
        }

		});
    }
```

# Generating the deb file and installing

```shell
cd openmediavault-pluginame
dpkg-buildpackage -us -uc
```

``Install``

```shell
dpkg -i openmediavault-pluginname_VERSION_all.deb
```