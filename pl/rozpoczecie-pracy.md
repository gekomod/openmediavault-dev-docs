---
title: Rozpoczęcie Pracy
description: 
published: 1
date: 2025-01-26T15:47:05.941Z
tags: 
editor: markdown
dateCreated: 2025-01-24T16:53:23.913Z
---


## Instalacja
1. **Pobierz obraz ISO**:
   - Pobierz najnowszy obraz ISO openMediaVault 7 z [oficjalnej strony](https://www.openmediavault.org/).

2. **Utwórz bootowalny nośnik**:
   - Użyj narzędzia takiego jak [Rufus](https://rufus.ie/) (Windows) lub `dd` (Linux) do utworzenia bootowalnego nośnika USB.

3. **Zainstaluj openMediaVault**:
   - Podłącz nośnik USB do serwera i uruchom go.
   - Postępuj zgodnie z instrukcjami instalatora, aby zainstalować system.
   
## Konfiguracja
1. **Logowanie do panelu administracyjnego**:
   - Po instalacji otwórz przeglądarkę i przejdź do `http://adres-ip-serwera`.
   - Zaloguj się przy użyciu domyślnych danych:
     - Login: `admin`
     - Hasło: `openmediavault`

2. **Konfiguracja sieci**:
   - Przejdź do `System -> Network -> Interfaces`, aby skonfigurować interfejsy sieciowe.

3. **Aktualizacja systemu**:
   - Przejdź do `System -> Update Management`, aby zainstalować najnowsze aktualizacje.
   
## Zarządzanie użytkownikami
1. **Dodawanie użytkowników**:
   - Przejdź do `Access Rights Management -> Users`, aby dodać nowych użytkowników.

2. **Zarządzanie grupami**:
   - Przejdź do `Access Rights Management -> Groups`, aby zarządzać grupami użytkowników.

## Zarządzanie dyskami
1. **Dodawanie dysków**:
   - Przejdź do `Storage -> Disks`, aby dodać i skonfigurować nowe dyski.

2. **Tworzenie systemów plików**:
   - Przejdź do `Storage -> File Systems`, aby utworzyć nowe systemy plików (np. ext4, BTRFS).

3. **Udostępnianie folderów**:
   - Przejdź do `Storage -> Shared Folders`, aby udostępnić foldery w sieci.
   
## Zarządzanie usługami
1. **Włączanie usług**:
   - Przejdź do `Services`, aby włączyć i skonfigurować usługi, takie jak SMB/CIFS, NFS, FTP itp.

2. **Konfiguracja SMB/CIFS**:
   - Przejdź do `Services -> SMB/CIFS`, aby skonfigurować udostępnianie plików w sieci Windows.

3. **Konfiguracja NFS**:
   - Przejdź do `Services -> NFS`, aby skonfigurować udostępnianie plików w sieci Linux.
   
## Wsparcie i pomoc
- **Oficjalna dokumentacja**: [openMediaVault Documentation](https://docs.openmediavault.org/)
- **Forum wsparcia**: [openMediaVault Forum](https://forum.openmediavault.org/)
- **GitHub**: [openMediaVault GitHub](https://github.com/openmediavault/openmediavault)