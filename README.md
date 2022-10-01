## GraalVM test

### Download GraalVM and tools

```shell
wget https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-22.2.0/graalvm-ce-java17-darwin-amd64-22.2.0.tar.gz
tar -xzf graalvm-ce-java17-darwin-amd64-22.2.0.tar.gz

VMDIR=/Library/Java/JavaVirtualMachines
GRDIR=graalvm-ce-java17-22.2.0

sudo mv $GRDIR $VMDIR/
sudo xattr -r -d com.apple.quarantine $VMDIR/$GRDIR

export JAVA_HOME=$VMDIR/$GRDIR/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH

gu install native-image
```

### Build Native Image

```shell
                        ~/graalvm-test $ ./gradlew clean build
                        ~/graalvm-test $ cd build/classes/java/main
~/graalvm-test/build/classes/java/main $ native-image App

~/graalvm-test/build/classes/java/main $ ./app
# The reversed string is: emosewa si egamI evitaN

~/graalvm-test/build/classes/java/main $ du -h app
# 12M app
```

### References

- https://www.graalvm.org/22.0/reference-manual/native-image/

