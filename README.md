Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Fringilla phasellus faucibus scelerisque eleifend donec pretium vulputate. Volutpat maecenas volutpat blandit aliquam etiam erat. Lorem mollis aliquam ut porttitor. Proin libero nunc consequat interdum varius sit amet mattis vulputate. Faucibus a pellentesque sit amet porttitor eget dolor. Scelerisque varius morbi enim nunc.

Erat imperdiet sed euismod nisi porta. Imperdiet nulla malesuada pellentesque elit eget gravida cum. Velit dignissim sodales ut eu sem integer vitae justo. 


 git push christiam master
Contando objetos: 20, listo.
Delta compression using up to 4 threads.
Comprimiendo objetos: 100% (12/12), listo.
Escribiendo objetos: 100% (20/20), 147.22 MiB | 2.28 MiB/s, listo.
Total 20 (delta 6), reused 20 (delta 6)
remote: Resolving deltas: 100% (6/6), done.
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
remote: error: Trace: c97b8c0f65b0dd1008b0377cdbc9b74d
remote: error: See http://git.io/iEPt8g for more information.
remote: error: File sc.16.tar.gz is 146.81 MB; this exceeds GitHub's file size limit of 100.00 MB
To github.com:MendivesChocos/orbis-example-training.git
 ! [remote rejected] master -> master (pre-receive hook declined)
error: fallo el push de algunas referencias a 'git@github.com:MendivesChocos/orbis-example-training.git'


 git gc
Contando objetos: 20, listo.
Delta compression using up to 4 threads.
Comprimiendo objetos: 100% (12/12), listo.
Escribiendo objetos: 100% (20/20), listo.
Total 20 (delta 6), reused 20 (delta 6)


git verify-pack -v .git/objects/pack/pack-e121f70e46f7ec3df6d405dfb4895762265c6af7.idx \
  | sort -k 3 -n \
  | tail -3
7044640436e9b16f956bbdc8d5329d10c8f07d62 blob   766 411 470939
2ce5eca830c1f68c365b5323677e7c37212eccf6 blob   479328 469875 1064
cfc3322ec593c88d0e4d68c312de3583ca741041 blob   153942735 153904153 471677


 git rev-list --objects --all | grep cfc3322ec593c88d0e4d68c312de3583ca741041
cfc3322ec593c88d0e4d68c312de3583ca741041 sc.16.tar.gz


 git log --oneline --branches -- sc.16.tar.gz

 git filter-branch --index-filter \
  'git rm --cached --ignore-unmatch sc.16.tar.gz' -- f3a6dc7^..
Rewrite f3a6dc74d8fd32278c93a5e9d4bbaec4d43c04c5 (1/3) (0 seconds passed, remaining 0 predicted)    rm 'sc.16.tar.gz'
Rewrite d270f6d507e5a9594183c7a64f112d7e798508fc (2/3) (0 seconds passed, remaining 0 predicted)    rm 'sc.16.tar.gz'
Rewrite 3bd289d96f8784ba7a3fd793364df80ebaaec1f3 (3/3) (0 seconds passed, remaining 0 predicted)    
Ref 'refs/heads/master' was rewritten


 rm -Rf .git/refs/original
 rm -Rf .git/logs/
 git gc



git count-objects -v
count: 0
size: 0
in-pack: 23
packs: 1
size-pack: 150759
prune-packable: 0
garbage: 0
size-garbage: 0


git push christiam master 
