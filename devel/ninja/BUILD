python configure.py --bootstrap &&

# test it
./ninja ninja_test &&
./ninja_test --gtest_filter=-SubprocessTest.SetWithLots &&

prepare_install &&
mkdir -p $DESTDIR/usr/bin &&
install -m755 ninja $DESTDIR/usr/bin/
