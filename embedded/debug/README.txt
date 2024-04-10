Part number:  M000-TEST-V9-8r
Description:  TEST OS release for M000 platform.
Release Date: 2024-04-04

Comments
--------
TEST OS release __placeholder__

Build steps - TEST
--------------------
The following steps have been followed to build this release, after coping the patches to the working directory:
scp miura1:/opt/share/Development/Dev-releases/_M000-OS/2024-04-04-M000-TEST-V9-8r-tmoore/*.patch ./

git clone miura1:/opt/Eagle-Proj/Eagle-AutoBuild
cd Eagle-AutoBuild/
git checkout M000-OS-V9-8
cd ..
Eagle-AutoBuild/autobuild $USER sasha_test pull M000-OS-V9-8

patch -p1 < M000-OS-V9-8.patch
Eagle-AutoBuild/autobuild $USER sasha_test all M000-OS-V9-8

sed -i "s/M000-TEST-V9-8r/M000-TEST-V9-8/" eagle.xml
./miura-cst-pc/miura-cst ./ --product

mkdir M000-TEST-V9-8r
cp -a M000-OS-VX-X.mlf M000-TEST-V9-8r/M000-TEST-V9-8r.mlf
cp -a M000-OS-VX-X.mlf.sig M000-TEST-V9-8r/M000-TEST-V9-8r.mlf.sig
tar -zcvf M000-TEST-V9-8r.tar.gz M000-TEST-V9-8r/
