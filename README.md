# usage

## if you don't have `Mojolicious`
    curl -L http://cpanmin.us | perl - --self-upgrade
    cpanm Mojolicious

## and run 
    git clone git://github.com/nqounet/p5-md2reveal.git
    cd p5-md2reveal
    mv md2reveal.conf.sample md2reveal.conf
    mv assets/example.md.sample assets/example.md
    mv assets/example.md.conf.sample assets/example.md.conf
    git submodule init
    git submodule update
    morbo md2reveal

