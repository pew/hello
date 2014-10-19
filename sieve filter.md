# dovecot sieve filter example

    require ["imap4flags", "fileinto", "reject", "regex"];
     
    # Catch mail tagged as Spam, except Spam retrained and delivered to the mailbox
    if allof (header :regex "X-DSPAM-Result" "^(Spam|Virus|Bl[ao]cklisted)$",
              not header :contains "X-DSPAM-Reclassified" "Innocent") {
      # Mark as read
    #  setflag "\\Seen";
      # Move into the Junk folder
      fileinto "Junk";
      # Stop processing here
      stop;
    }
     
    if address :all :is ["to", "cc"] "user@domain.com" {
      fileinto "folder1";
    } elsif address :all :is ["to", "cc"] "user2@domain.com" {
      fileinto "folder2";
    } elsif address :all :is ["to", "cc"] "webappsec@securityfocus.com" {
      fileinto "mailing lists.securityfocus";
    } elsif address :all :is ["to", "cc"] "bugtraq@securityfocus.com" {
      fileinto "mailing lists.securityfocus";
    }