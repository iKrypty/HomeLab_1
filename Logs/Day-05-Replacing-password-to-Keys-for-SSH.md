Day 5: 11/12/26 Securing Pi by using SSH Keys and Log Journaling:

/* Had to put the project to the side due to some personal matters including school, finished midterms on a good note though! */

 * Generated an Ed25519 key pair and protected it with a passphrase
 * Copied the public key to the Pi and confirmed key-based login
 * Found that 50-cloud-init.conf was enabling password login, and overrode it with a higher-priority 01-hardening.conf
 * Verified with sshd -T, and proved passwords are rejected with “Permission denied (publickey)”
 * Enabled Persistant Logs by overriding "/etc/systemd/journald.conf.d", put on a 100M cap to limit SD card wear.
 * Added verification to the Persistant Logs using Machine ID.

What I learned: 
 * Ed25519 keys are small, fast, and secure. SSH proves my identity by signing a challenge with my private key, and the key never leaves my PC.
 * Always verify the effective config (sshd -T) instead of assuming a file was applied.
 * Config priority differs between programs: SSH uses the first value it reads, while systemd drop-ins use the last.
 * Keep wroking on session open while changing remote access settings, so a mistake doesn't lock you out.
 * Logs stored on the same machine can be deleted by an attacker. The next step is sending logs to a central server (like Wazuh).

There was a lot of trial and error using the commands and going back and forth to see if config files were actually applied or not. Claude was a big help or else it would have taken me a couple more hours!

Total time spent: 2.5 hours
