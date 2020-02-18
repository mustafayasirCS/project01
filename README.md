# CS 102 Project for 2019-2020 Spring Semester in Bilkent

## Project Proposals

#### Map (?)
To be explained
* Resources
  * [About Open Street Map](https://www.openstreetmap.org/about)
  * Open Street Map [export map](https://www.openstreetmap.org/export#map=14/39.8726/32.7637)
  * Open Street Map [Develop-Wiki](https://wiki.openstreetmap.org/wiki/Develop)

#### ~~High availability back-up program~~

##### Main features

1. Efficiency
   * Definitely read [this](https://www.tarsnap.com/deduplication-explanation.html). Basically only the data that has changed (added, modified, deleted, etc.) is transferred between back-up runs.
   * This is done by deduplication based on [content-defined chunking](https://restic.net/blog/2015-09-12/restic-foundation1-cdc) which is a way to reduce the number of bytes stored and transmitted: Each file is split into a number of variable length chunks and only chunks that have never been seen before are (compressed and) added to the repository.
   * Algorithm details & choices:
      * CDC=[Buzhash](https://en.wikipedia.org/wiki/Rolling_hash#Cyclic_polynomial)
      * Compression=[Zstandard](https://facebook.github.io/zstd/)
      
2. Confidentiality/Security: We encrypt the data because we assume data the location where the backup data is stored is **not** a trusted environment. 
   * Algorithm details & choices:
      * Cipher=[ChaCha20/(8)](https://en.wikipedia.org/wiki/Salsa20#ChaCha_variant)
      * Cipher=[Aegis-128](https://competitions.cr.yp.to/caesar-submissions.html)
      
      * KDF=[Argon2id](https://github.com/p-h-c/phc-winner-argon2)
      
3. Integrity/Verifiability
   * We validate the data for accidental or intentional tampering (added, modified, deleted, etc.) because we assume data the location where the backup data is stored is **not** a trusted environment.
   * This is done by [cryptographic message authentication codes](https://en.wikipedia.org/wiki/Message_authentication_code). 
   ![Alt text](./MAC.svg)
   * Algorithm details & choices:
      * MAC=[BLAKE3 hash function (keyed mode)](https://github.com/BLAKE3-team/BLAKE3)
      
4. Availability/Durability: We encode the data with a forward error correction algorithm and disturbute it to our back-up targets.
   * Algorithm details & choices:
      * FEC=[Reed-Solomon](https://en.wikipedia.org/wiki/Reed%E2%80%93Solomon_error_correction)
      * FEC=[RaptorQ](https://github.com/openrq-team/OpenRQ/wiki/%22What-is-RaptorQ%3F%22)
      
      * Hybrid-FEC=[STAIR](https://dl.acm.org/doi/pdf/10.1145/2658991?download=true)
      
      * [SoK paper comparing them (2010)](https://www.usenix.org/legacy/event/fast09/tech/full_papers/plank/plank.pdf)

* Referance programs & algorithms (Skim them):
   * <https://restic.readthedocs.io/en/latest/100_references.html#design>
   * <https://borgbackup.readthedocs.io/en/stable/internals.html>
   * <https://www.tarsnap.com/>
   * <http://0pointer.net/blog/casync-a-tool-for-distributing-file-system-images.html>
   * <https://github.com/systemd/casync/blob/master/README.md>
   * <https://github.com/redox-os/tfs/blob/master/README.rst#design-goals>

#### ~~~~Android App for Bilkent Library Catalog~~
To be explained

#### ~~~~~~~~Product Tracing System~~~~~~
To be explained

#### ~~~~General NFC Manager~~
To be explained

#### Code Checking
Code review tool to help students and TAs find and understand problems with CS101-CS102 code?

## Resources

### Android Application development
+ [Build Your First Android App in Java by Google](https://codelabs.developers.google.com/codelabs/build-your-first-android-app/#0)

### Design and Style Guidelines
+ In this project we strictly follow certain rules which are gathered together by David Davenport:
   - design and implementation rules which can be found  [here](https://web.archive.org/web/20170930094137/http://www.cs.bilkent.edu.tr/~david/cs101/practicalwork/2010/JavaLabs.htm),
   - and we have rules on OOP [here](https://web.archive.org/web/20170930110056/http://www.cs.bilkent.edu.tr/~david/cs101/practicalwork/2010/JavaOOPLabs.htm),
   - and of course a strict style guide lines [here](https://web.archive.org/web/20170930110102/http://www.cs.bilkent.edu.tr/~david/cs101/practicalwork/2010/styleguidelines.htm).


+ First line of each and every source code starts with packaging,
  + [Further reading](https://www.geeksforgeeks.org/packages-in-java/) that you may or may not find useful 
+ continues with importings after a blank line
  ```
  package superPack.pack;
  
  import superPack.pack.src.Class;
  import java.util.Xxxx;
  ```
### About javadoc comments
***Usage of javadoc comments just before defining classes, constructors and methods is mandatory.***
1. Examples of styling
   * Before Classes
   ```
   /**
    * This class (or object) have blah blah blah and can do blah blah blah
    * @author Muhammed Can Küçükaslan
    * @version 2020.02.14 added blah blah featue and fixed blah blah bugs
    *          2020.01.14 Created with blah blah features and properties 
    */
    public class Example {
    ...
    }
   ```
   
   * Before constructors
    ```
    /**
    * This generates a ClassName object and sets default or given (by parameters) values to the properties
    * @param paramName is blah blah blah
    */
   public ClassName( Object paramName) {
   ...
   }
    ```
   * Before Methods
    ```
    /**
    *  This method does blah blah blah
    * (if an instance method) changes blah blah properties in blah blah way
    * @param paramName is blah blah blah
    * @return a logical value which is ObjectType (or a primitive value)
    */
   public ObjectType getName( Object paramName) {
   ...
   }
   ```
