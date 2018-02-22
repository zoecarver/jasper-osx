# Jasper on OSX

1. Make sure that you have brew installed:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

1. Install python2 if it is not already installed:

```bash
brew install python2
```

1. Use pip to install the requirements:

```bash
sudo pip2 install --upgrade setuptools
sudo pip2 install -r jasper/client/requirements.txt
```

1. Install `portaudio` and `pyaudio`

```bash
brew install portaudio
sudo pip2 install pyaudio
```

1. Now you may go on to configure jasper

------

### Pocket Sphynx

1. Install CMUCLMTK

   1. If necessary install svn (mine was not a recent enough version)

   ```bash
   brew install svn
   ```

   1. Install autoconf and libtool

   ```bash
   brew install automake
   brew install libtool
   ```

   1. Install CMUCLMTK

   ```bash
   svn co https://svn.code.sf.net/p/cmusphinx/code/trunk/cmuclmtk/
   cd cmuclmtk/
   ./autogen.sh && make && sudo make install
   cd ..
   ```

2. Install pocket sphynx

```brew
brew install cmu-pocketsphinx
```

1. Install phonetisaurus

   1. install openfst

      ```bash
      brew install https://raw.githubusercontent.com/Homebrew/homebrew-science/08b575e5b63a15489eb2aa91e4282ac574eefedb/openfst.rb
      ```

   2. Download the tarball

      ```bash
      wget https://www.dropbox.com/s/1bgavg07qx8fe5w/phonetisaurus-googlecode-archive.tgz
      ```

   3. Untar it

      ```bash
      tar -xf phonetisaurus-googlecode-archive.tgz
      ```

   4. Enter the directory and untar `g2p2rnn`

      ```bash
      cd phonetisaurus-googlecode-archive/downloads
      tar -xf g2p2rnn.tgz
      ```

   5. Enter that directory and delete the make file

      ```bash
      cd g2p2rnn
      rm Makefile
      ```

   6. Grab an updated make file for OS X

      ```bash
      wget new.Makefile
      ```

   7. make and copy to `/usr/local/bin`

      ```bash
      sudo make
      sudo cp phonetisaurus-g2p /usr/local/bin/phonetisaurus-g2p
      ```


1. Build the model

```bash
wget https://www.dropbox.com/s/kfht75czdwucni1/g014b2b.tgz
tar -xf g014b2b.tgz
cd g014b2b/
./compile-fst.sh
cd ..
mv g014b2b ~/phonetisaurus
```

1. modify `g2g.py` to work with our version of `phonetisaurus-g2p`