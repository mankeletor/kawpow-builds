# kawpow-builds
These are the most mined kawpaw coins builds for linux (deb/ubuntu and based distros)

# Available scripts

#meowcoin 
#neoxa
#clore
#paprikacoin

# Ravencoin

Ravencoin guys did it right with binary realease but still no deb package.

Anyway this is easy to fix once you got https://github.com/RavenProject/Ravencoin/releases/download/v4.6.1/raven-4.6.1-7864c39c2-x86_64-linux-gnu.tar.gz

tar xf raven-4.6.1-7864c39c2-x86_64-linux-gnu.tar.gz; cd raven-4.6.1-7864c39c2

mkdir usr; mv * usr; 

find -type d -name 'man' -exec find {} -type f \; | while read line; do gzip -9 $line; done

find -type f | xargs file | grep -e "executable" -e "shared object" | grep ELF \

  | cut -f 1 -d : | xargs strip --strip-unneeded 2> /dev/null

tar cf raven-4.6.1.tar ./

alien raven-4.6.1.tar raven-4.6.1.deb

(it should works but I didn't test it)


# Linux wallet releases doesn't worked

I decided to work around the original scripts on doc/build_with_db 4_linux.sh once the binary release doesn't work for me. 
I noticed the only files on that releases was like 3 binaries but the statics and dinamics libs needed (and many other files)
for run the program are not present on it.

# Start build
You must to be sure to have alien installed

sudo apt install alien

get the <source_tarball>.tar.gz

tar xf <sorce_tarball>.tar.gz

copy the build script on uncompressed <source_tarball_dir>

cd <source_tarball_dir>

chmod 755 build_script.sh

./build_script.sh

If everything goes right a debian package should be created on tmp-destdir/<packagename>.deb

Ignore the alien warning "file not found"

# Got Slack?

With some mods you can turn this build scripts into SlackBuilds, Why? I took some helps from slackbuilds cos Pat did it very right from beginning!
