# level 1 ---> level 2
in order to view a dashed filename you have to specify the full location
**pass:** CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

# level 2 ---> level 3
**pass:** UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

# level 3 ---> level 4
**pass:** pIwrPrtPN36QITSp3EQaw936yaFoFgAB

# level 4 ---> level 5
use file -b to get the type of file content and then cat using the full path as it is a dashed file
**pass:** koReBOKuIDDepwhWk7jZC0RTdopnAYKh

# level 5 ---> level 6
find - size 1033b means 1033 blocks of 512bytes but we want 1033 bytes and not executable so it's rather find - size 1033c ! -executable
**pass:** DXjZPULLxYr17uwoI01bNLQbtFemEgo7

# level 6 ---> level 7
error redirection from standard output to /dev/null to remove uniteresting output 
**pass:** HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

# level 7 ---> level 8
**pass:** cvX2JJa4CFALtqS87jk27qwqGhBM9plV

# level 8 ---> level 9
uniq only eliminates adjacent lines so in order to eliminate all unique line we have to sort it first:
sort data.txt | uniq -u
**pass:** UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

# level 9 ---> level 10
 strings data.txt |grep -e =
 **pass:** truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

# level 10 ---> level 11
**pass:** IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

# Level 11 ---> level 12
**pass:** 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

# Level 12 ---> level 13
use mktemp -d /tmp/.XXX => created /tmp/.ju9 for me
decompress ike a hundred times:
1. use file filename to get the type of file
2. decompress accoding to the file type:
    1. gunzip need the file to have the .gz extension so rename the file first
    2. tar doesn't care about the file extension so just use tar -xf filename
**pass:** 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL