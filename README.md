# Signum release check

## History
In Jan 5th 2023, signum-node v3.6.0 was released including hidden changes in source code there weren't documented. This behaviour was not acceptable by me (deleterium), and I've left the dev team. In order to add transparency and more confidence for next releases, I'm inspecting each mainnet release to check if my expectations of an open source project are met.

## Acknowledgment of work
Each version has a lot of new code and it is a huge work. For sure most of code is good and follow my expectations. I would like to thanks the people creating code for signum-node. 

## Expectations
* No obfuscated code or variables with wrong names
* No hidden code: commit messages must match the intended result
* Use the SIP's: major changes in signum-node (the ones that lead to hard forks) shall be documented in https://github.com/signum-network/SIPs
* Document user options
* Correct release notes: major changes are included in signum-node release notes

## Issues at v3.6.0

### Issue 1
Commit: https://github.com/signum-network/signum-node/commit/3eaa1ebffcbc579f9b247352bd307cb95c2cb7cf

Network fork not documented: Blocking accounts that does not have public key set for more than one year.

ALERT! Commit message does not reveal this intended changed.

### Issue 2
Commit: https://github.com/signum-network/signum-node/commit/3eaa1ebffcbc579f9b247352bd307cb95c2cb7cf

Network fork not documented: Blocking ten accounts with public key already set. Accounts are: S-R8SQ-TUEM-DTHQ-7ATA3, S-GH7A-GDMN-7SAY-A5FPE, S-PFVF-NXAR-JGQM-BYGWV, S-P2Q6-2CMM-DAUJ-5HWTC, S-65RV-RLLM-RLFY-75JAG, S-PASP-C8J7-H9Z3-AYCFA, S-DZ39-9EQH-FHUK-D6Y5N, S-P2Q6-2CMM-DAUJ-5HWTC, S-A76S-7HK7-MFXA-9UCLF and S-BEAE-PPSP-JKE7-FQ5Z5.

ALERT! Commit message does not reveal this intended changed. The accounts are obfuscated at the line:
`public static final Prop<String> BRS_PK_CHECKS = new Prop<>("node.pkChecks", "169b3b99ce28a350;a83c47e772a35586;6db77a51a7def19d;c4823aa7028f6735;fb0e32a5bc032257;15a35aa0515e3584;27fcf52c3bc40fba;c4823aa7028f6735;981454e22b5ac976;0cb15471ad76fcd1;");`

### Issue 3
Commit: https://github.com/signum-network/signum-node/commit/3eaa1ebffcbc579f9b247352bd307cb95c2cb7cf

New configuration options not documented: `brs.pkBlock.startBlock`, `brs.pkBlocksPast` and `node.pkChecks`.

New options can be used in `node.properties` file, but they aren't documented in `node-default.properties`.

### Issue 4
Commit: https://github.com/signum-network/signum-node/commit/c01f8600610c987422ab3dcf47d130501c8e5483

Related to the issue 2. Added new account to be blocked S-MBQV-8MQ5-HLVX-DJ4S5

ALERT! Commit message does not reveal this intended changed. The accounts are obfuscated at the line:
`public static final Prop<String> BRS_PK_CHECKS = new Prop<>("node.pkChecks", "dba639ec3450e0b1;169b3b99ce28a350;a83c47e772a35586;6db77a51a7def19d;c4823aa7028f6735;fb0e32a5bc032257;15a35aa0515e3584;27fcf52c3bc40fba;c4823aa7028f6735;981454e22b5ac976;0cb15471ad76fcd1;");`

## Issues at v3.7.0

### Issue 5
Commit: https://github.com/signum-network/signum-node/commit/c8780c6ba16f3944b62965fd976124a6f0068831

Network fork not documented: implemented new smart contract API GET_ACCOUNT_BALANCE.

This AT API change is not documented in a SIP's.


## Suggestions to close issues

**Issue 1**
* Document the fork creating a SIP.

**Issue 2**
* Document the blocked accounts in a SIP
* Rename the property, in a way that the name reflects its meaning (not pkChecks, but blockedAccounts)
* Change the property default values to be easy to know the blocked accounts, i.e.: changing hexadecimal values to ID.

**Issue 3**
* Add the default values in `node-default.properties` file, also with a brief description. Consider hard code the values to source code if it is not intented for users to change them.

**Issue 4**
* Fix the issue 2

**Issue 5**
* Document new Smart Contrac API in a SIP.
* Fix the release notes to include this change.
