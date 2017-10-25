# Decoding

Decoding is tough, especially if you don't know what to look for. Hopefully this cheatsheet helps you with that.

## Identifying Hashes
Sometimes in your Cyber Security adventures you might come across some weird string that you might suspect to be some sort of encoded data.

Here are some tools that might help you identify what kind of encoding was used.
- [hashID](https://github.com/psypanda/hashID)
- [Hash Type Checker](https://md5hashing.net/hash_type_checker/)

Next, look for context clues to help you determine what type of hashing was used.

If these don't work, you might have to do some manual digging.
Here's a table of encoding types that might give you some hints as to what it is.

Key:
- [1] Since the hashing requires not only a password but also a salt (or a user name), which is unique for each user, the attack speed for such hashes will decline proportionally to their count (for example, attacking
100 hashes will go 100 times slower than attacking one hash).
- [2] The hash is to be loaded to the program in full, to the "Hash" column - the program will automatically extract the salt and other required data from it.
- [3] The ':' character can be used as salt; however, since it is used by default for separating hash and salt in PasswordsPro, it is recommended that you use a different character for separating fields; e.g., space.
- [4] Salt can contain special characters - single or double quotes, as well as backslash, which are preceded (after obtaining dumps from MySQL databases) by an additional backslash, which is to be removed manually. For
example, the salt to be loaded to the program would be a'4 instead of a\'4, as well as the salts a"4 instead of a\"4 and a\4 instead of a\\4.

|Name|Example|Use|Length|Description|Algorithm|Key|
|-|-|-|-|-|-|-|
|DES(Unix)|IvS7aeT4NzQPM|Used in Linux and other similar OS|13 characters|The first two characters are the salt (random characters; in our example the salt is the string "Iv"), then there follows the actual hash||[1] [2]|
|Domain Cached Credentials|b474d48cdfc4974d86ef4d24904cdd91|Used for caching passwords of Windows domain|16 bytes||MD4(MD4(Unicode($pass)).Unicode(strtolower($username)))|[1]|
|MD5(Unix)|$1$12345678$XM4P3PrKBgKNnTaqG9P0T/|Used in Linux and other similar OS|34 characters|The hash begins with the $1$ signature, then there goes the salt (up to 8 random characters; in our example the salt is the string "12345678"), then there goes one more $ character, followed by the actual hash|Actually that is a loop calling the MD5 algorithm 2000 times|[1] [2]|
|MD5(APR)|$apr1$12345678$auQSX8Mvzt.tdBi4y6Xgj.|Used in Linux and other similar OS|37 characters|The hash begins with the $apr1$ signature, then there goes the salt (up to 8 random characters; in our example the salt is the string "12345678"), then there goes one more $ character, followed by the actual hash|Actually that is a loop calling the MD5 algorithm 2000 times|[1] [2]|
|MD5(phpBB3)|$H$9123456785DAERgALpsri.D9z3ht120|Used in phpBB 3.x.x.|34 characters|The hash begins with the $H$ signature, then there goes one character (most often the number '9'), then there goes the salt (8 random characters; in our example the salt is the string "12345678"), followed by the actual hash|Actually that is a loop calling the MD5 algorithm 2048 times|[1] [2]|
|MD5(Wordpress)|$P$B123456780BhGFYSlUqGyE6ErKErL01|Used in Wordpress|34 characters|The hash begins with the $P$ signature, then there goes one character (most often the number 'B'), then there goes the salt (8 random characters; in our example the salt is the string "12345678"), followed by the actual hash|Actually that is a loop calling the MD5 algorithm 8192 times|[1] [2]|
|MySQL|606717496665bcba|Used in the old versions of MySQL|  8 bytes|The hash consists of two DWORDs, each not exceeding the value of 0x7fffffff|||
|MySQL5|*E6CC90B878B948C35E92B003C792C46C58C4AF40|Used in the new versions of MySQL|20 bytes|SHA-1(SHA-1($pass))|The hashes are to be loaded to the program without the asterisk that stands in the beginning of each hash||
|RAdmin v2.x|5e32cceaafed5cc80866737dfb212d7f|Used in the application Remote Administrator v2.x|16 bytes|The password is padded with zeros to the length of 100 bytes, then that entire string is hashed with the MD5 algorithm|||
|MD5|c4ca4238a0b923820dcc509a6f75849b|Used in phpBB v2.x, Joomla version below 1.0.13 and many other forums and CMS| 16 bytes|Same as the md5() function in PHP|||
|md5($pass.$salt)|6f04f0d75f6870858bae14ac0b6d9f73:1234|Used in WB News, Joomla version 1.0.13 and higher|16 bytes|   ||[1]|
|md5($salt.$pass)|f190ce9ac8445d249747cab7be43f7d5:12|Used in osCommerce, AEF, Gallery and other CMS|16 bytes|||[1]|
|md5(md5($pass))|28c8edde3d61a0411511d3b1866f0636|Used in e107, DLE, AVE, Diferior, Koobi and other CMS|16 bytes|  |||
|md5(md5($pass).$salt)|6011527690eddca23580955c216b1fd2:wQ6|  Used in vBulletin, IceBB|16 bytes|||[1] [3] [4]|
|md5(md5($salt).md5($pass))|   |81f87275dd805aa018df8befe09fe9f8:wH6_S|Used in IPB|16 bytes| |[1] [3]|
|md5(md5($salt).$pass)|816a14db44578f516cbaef25bd8d8296:1234|Used in MyBB|16 bytes|||[1]|
|md5($salt.$pass.$salt)|a3bc9e11fddf4fef4deea11e33668eab:1234|Used in TBDev|16 bytes|||[1]|
|md5($salt.md5($salt.$pass))|1d715e52285e5a6b546e442792652c8a:1234|Used in DLP|16 bytes|   ||[1]|
|SHA-1|356a192b7913b04c54574d18c28d46e6395428ab|Used in many forums and CMS|20 bytes|Same as the sha1() function in PHP| ||
|sha1(strtolower($username).$pass)| Admin:6c7ca345f63f835cb353ff15bd6c5e052ec08e7a|Used in SMF|20 bytes|||[1]|
|sha1($salt.sha1($salt.sha1($pass)))|cd37bfbf68d198d11d39a67158c0c9cddf34573b:1234|Used in Woltlab BB|20 bytes|||[1]|
|SHA-256(Unix)|$5$12345678$jBWLgeYZbSvREnuBr5s3gp13vqiKSNK1rkTk9zYE1v0|Used in Linux and other similar OS|55 characters|The hash begins with the $5$ signature, then there goes the salt (up to 8 random characters; in our example the salt is the string "12345678"), then there goes one more $ character, followed by the actual hash|Actually that is a loop calling the SHA-256 algorithm 5000 times|[1] [2]|
|SHA-512(Unix)|$6$12345678$U6Yv5E1lWn6mEESzKen42o6rbEmFNLlq6Ik9X3reMXY3doKEuxrcDohKUx0Oxf44aeTIxGEjssvtT1aKyZHjs|Used in Linux and other similar OS|98 characters|The hash begins with the $6$ signature, then there goes the salt (up to 8 random characters; in our example the salt is the string "12345678"), then there goes one more $ character, followed by the actual hash| Actually that is a loop calling the SHA-512 algorithm 5000 times|[1] [2]|
|SHA-1(Django) = sha1($salt.$pass)|sha1$12345678$90fbbcf2b72b5973ae42cd3a19ab4ae8a1bd210b|12345678 is salt (in the hexadecimal format), 90fbbcf2b72b5973ae42cd3a19ab4ae8a1bd210b is SHA-1 hash.|||
|SHA-256(Django) = SHA-256($salt.$pass)| sha256$12345678$154c4c511cbb166a317c247a839e46cac6d9208af5b015e1867a84cd9a56007b|12345678 is salt (in the hexadecimal format),154c4c511cbb166a317c247a839e46cac6d9208af5b015e1867a84cd9a56007b is SHA-256 hash.|   |   |
|SHA-384(Django) = SHA-384($salt.$pass)|sha384$12345678$c0be393a500c7d42b1bd03a1a0a76302f7f472fc132f11ea6373659d0bd8675d04e12d8016d83001c327f0ab70843dd5|12345678 is salt (in the hexadecimal format), c0be393a500c7d42b1bd03a1a0a76302f7f472fc132f11ea6373659d0bd8675d04e12d8016d83001c327f0ab70843dd5 is SHA-384 hash.|   |   |
|SHA-1(ManGOS)|   | ||  |sha1(strtoupper($username).':'.$pass)|   |
|SHA-1(ManGOS2)|   | ||  |sha1($username.':'.$pass)|   |
|MD5(Custom)|   | ||  |'=='.md5(md5(md5($pass).md5($pass).md5($pass).md5($pass)))|   |
|md5(3 x strtoupper(md5($pass)))|   | ||  |md5(strtoupper(md5(strtoupper(md5(strtoupper(md5($pass)))))))|   |

Other hash encoding resources
- http://openwall.info/wiki/john/sample-hashes

## Steganography
> The practice of concealing messages or information within other nonsecret text or data

For every file given, use UNIX's `file` command to first determine what type of file you are looking at.

Some other useful commands would be `strings` or `grep`.

Some tools that are applicable to all files that might have stuff hidden in them would be `foremost` or `binwalk`.

### Images
Some tools specific to images would be `stepic`, `steghide`, or `stegdetect`. You might also want to view the EXIF data with `exiftool` or `exifprobe`.

Interesting writeups to get you thinking
- https://github.com/ctfs/write-ups-2014/tree/master/plaid-ctf-2014/doge-stege
- https://github.com/ctfs/write-ups-2015/tree/master/9447-ctf-2015/steganography/gife-up-now

Tools
- [Digital Ink Toolkit](http://diit.sourceforge.net/)
- [GIMP](https://www.gimp.org/)
- [Photoshop](http://www.adobe.com/products/photoshop.html)

### Audio

Intersting writeups to get you thinking
- https://github.com/ctfs/write-ups-2014/tree/master/asis-ctf-quals-2014/sound-zoo
- http://deepinsecurity.blogspot.com/2013/10/sharif-ctf-quals-2013-steganography-200.html

Tools
- [Audacity](http://www.audacityteam.org/)
- [MP3stego](http://www.petitcolas.net/steganography/mp3stego/)

Thanks for reading!
