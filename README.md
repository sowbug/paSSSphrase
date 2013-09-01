paSSSphrase
===========

Split a strong passphrase among friends using Shamir's secret sharing, then etch it into metal so it'll last longer than you will.

Problem
=======

You accept the truth that you're going to die someday, preferably far in the future. Like most of us, you have digital secrets that you want to pass to your successors. But while you're alive, your secrets should stay secret. And you really don't want your stuff to be discovered by the maid or your creepy roommate (meaning that printing them out unencrypted is a bad idea), or stolen by malware (meaning that keeping them online is a bad idea).

Overview of Solution
====================

* Create a strong passphrase that cannot be guessed within the expected lifetime of the universe.
* Create a GPG keypair. Use the passphrase to protect the private key.
* Email the keypair (including the private key) to a bunch of people, put it on Dropbox or Google Drive, print it out, paint it on your roof, whatever. The private half is protected by the passphrase, so it's useless to recipients. You're sending it out so that there will be plenty of copies in the world.
* Divide the passphrase into shares using [Shamir's Secret Sharing](http://en.wikipedia.org/wiki/Shamir's_Secret_Sharing) (SSS).
* Using [electro-etching](http://en.wikipedia.org/wiki/Electroetching) (sort of the opposite of electroplating), etch the passphrase shares into metal tokens that are durable enough to survive any catastrophe that human civilization could also survive.
* Give one token to each of five friends or family. Avoid picking people who have a tendency to conspire.
* Now you're ready to start protecting your secrets. GPG-encrypt them with the public key. Give copies of the encrypted output to your successors.

Details of Solution
===================

* SSS allows a subset of the tokens to reconstruct the secret. By default, this tool generates five tokens, where three are the threshold for recovery.
* It's assumed that QR-code readers, ssss, and GPG will exist in the future. If not, your successors will need a magnifying glass, a calculator, and a lot of free time.
* You get to choose the metal for etching. Aluminum is easy to etch and has predictable oxidization characteristics. Stainless steel is more durable but a lot harder to etch. I haven't tried copper or brass. It's my understanding you'll kill yourself if you try zinc (which is what "galvanization" means, so be careful).

What Happens When You Die?
==========================

You will have given the token-holders instructions to deliver the tokens to your successors upon your death. Hopefully one of them will be smart enough to figure out that the "ssss-combine" language on the tokens is a Unix shell command. If so, your successors will successfully reconstruct the passphrase. At that point, they will deduce that this string of gibberish must be the passphrase to that "Please Keep This Email Forever" email attachment you sent them way back in 2013, and further that the attachment is the key to all the encrypted stuff you've been emailing them ever since.

Would your children/spouse/corporate partners actually do this? If you're detail-oriented and visionary enough to still be reading this README, then you were probably successful enough to amass some serious wealth while you were alive, including pure-digital assets such as Bitcoin. Thus it's safe to assume that they'll have the motivation to figure out this puzzle.

Installation Instructions
=========================

1. Install Ruby.
1. Install the Ruby gems rmagick and qrencoder.
1. Install [ssss](http://point-at-infinity.org/ssss/), which is available on most Linux distributions via your package manager, and OSX through Homebrew.
1. As a trial, run passsphrase. If you have all the system dependencies correct, you'll end up with a few PNG files in the current directory.

Generation and Etching Instructions
===================================

1. Secure your computer: unplug it from the internet and remove your pet virus collection.
1. Close the shades, kick everyone out of the house.
1. cd to a temporary directory -- **not** to one that's automatically synced to the cloud (e.g., Dropbox).
1. Run passsphrase.
1. Print exactly one copy of etching-pattern.png.
1. Securely delete all the generated PNG files. You really won't need them again; if the process messes up, you'll regenerate a new passphrase.
1. Follow the [Bitcoin Wallet Instructable](http://instructables.com/id/A-Stainless-Steel-Bitcoin-Wallet/) or [any other](http://steampunkworkshop.com/electroetch.shtml) electroetching tutorial.
1. Cut the metal into individual tokens with tin snips.
1. Distribute the tokens to the token-holders.
1. Live a long life, secure in the knowledge that your secrets will be correctly transferred upon your death.

Tips From My Experience with Etching
====================================

* Use Staples 633215 gloss-finish heavyweight color laser printer paper.
* Use the best laser printer you can find. Print black-and-white. Choose the highest resolution the printer has, and if the printer dialog lets you pick, choose the thickest paper setting, which usually leads to the most toner being deposited on the paper.
* Use half of a 5" x 7" aluminum shingle. The paSSSphrase utility will generate a 7" x 2.5" pattern. Don't use galvanized steel unless you really know what you're doing, because vaporized zinc will *mess you up*!
* Sand the metal with 400-grit paper on both sides. Both sides are important: one for the toner side, the other to ensure conductivity with the cathode.
* After sanding, soak the metal in any mildly acidic solution for about five minutes. I used toilet-bowl cleaner that listed hydrochloric acid among its ingredients.
* Clean the metal with pure acetone and a paper towel.
* Clean the metal once again with 91% isopropyl alcohol and another paper towel. Don't touch the metal with your fingers after cleaning.
* Buy or borrow a laminator rather than trying to use a clothes iron. This step is significantly different from many of the tutorials you'll find on the web.
* Affix the paper to the metal with kapton tape.
* Run the metal through the laminator at least eight times. I recommend folding the metal/paper combination in a regular page of paper to protect the laminator.
* Soak the metal/paper combo in hot soapy water for about 5 minutes, or until you see that all the paper has absorbed water.
* Remove the paper by rubbing with your fingers. Avoid rubbing the edges of the metal toward the center, because that direction tends to unseat the toner. If you accidentally destroy any of the QR codes, go back up to Step 1.
* Because I used aluminum, I needed a solution of [copper sulfate and table salt](http://www.nontoxicprint.com/electroetching.htm) rather than plain salt that steel requires.
* I etched in a plastic peanut-butter jar at 9.3 volts for exactly five minutes. I saw about 1.6 amps current throughout.
* About every 90 seconds I brushed the surface of the tokens with an old toothbrush to remove the brown gunk.
* Clean afterward with acetone.
* Consider laminating the tokens to reduce oxidization risk, as well as to cover the sharp edges.
