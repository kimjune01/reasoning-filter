Apple's assertion it "cannot intercept" iMessages is technically accurate but fundamentally misleading. Researchers at Quarklab had identified vulnerabilities in the iMessage protocol, including weaknesses in the trust model and key exchange mechanisms. Additionally, iCloud backups containing iMessages could be accessed by Apple itself.

The crux of the vulnerability lies in Apple's control of the entire technical stack — iOS, the iMessage application, SSL certificates, and key exchange protocols. Without certificate pinning (a security measure where only specific certificates are trusted), iMessage becomes vulnerable if an attacker can obtain a trusted Apple SSL certificate and intercept the key exchange.

Apple correctly answers whether it currently reads messages — it doesn't. However, the company could relatively easily engineer backdoor access if compelled. The simplest method would involve adding a "ghost" iMessage device to receive copies of messages while suppressing notifications of new device additions.

The issue isn't whether Apple can intercept messages technically, but whether it would if legally pressured. Given the reputational damage from potential leaks, Apple currently doesn't intercept messages but could add this capability with minimal code changes.

True security assurance would require open-source code auditable by experts and user-managed encryption keys — measures most users wouldn't realistically adopt today but might demand as surveillance concerns grow.
