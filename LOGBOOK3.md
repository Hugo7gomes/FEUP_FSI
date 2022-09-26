
# Trabalho realizado na Semana #3

## Identificação

- Microsoft Windows Netlogon Remote Protocol is a remote procedure interface that is used for user and machine authentication on domain-based networks
- The versions 14.04, 16.04, 18.04 and 20.04 of Ubuntu Linux and the versions 1903, 1909 and 2004 of Windows Server 2016 were the main ones affected.
- The attacker can set an empty password for the domain controller's Active Directory computer account, causing a denial of service, and potentially allowing the attacker to gain domain administrator privileges.

## Catalogação

- Found by Tom Tervoort of Secura, in September 2019, with a cvss score of 9.3/10. 
- Microsoft patched this exploit in two phases: the first one on August 11th 2020 which adressed the security issue in Active directory domains and trusts, as well as Windows devices  
- The second patch occurred on February 9th 2021 in which enforcement mode was enabled on all Windows Domain Controllers

## Exploit

- The issue exists in the usage of AES-CFB8 encryption for Netlogon sessions. 
- The AES-CFB8 standard requires that each “byte” of plaintext have a randomized initialization vector (IV), blocking attackers from guessing passwords.
- Netlogon’s ComputeNetlogonCredential function sets the IV to a fixed 16 bits – not randomized –  meaning an attacker could control the deciphered text.
- https://github.com/risksense/zerologon

## Ataques

- Darktrace AI detected a cyber-attack on a healthcare company in Europe exploiting this very flaw.
- Iranian APT group Mercury — which historically has targeted government organizations, particularly in the Middle East — had been using the ZeroLogon flaw in active campaigns for two weeks.

