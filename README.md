```java
    static long arrayToLong(byte[] arr, int startPos) {
        if (startPos < 0) {
            throw new IllegalArgumentException("startPos must not be negative. was: " + startPos);
        }
        if ((arr.length - startPos) < 8) {
            throw new IllegalArgumentException("Array has to have at least 8 bytes after startPos. arr.length was: " + arr.length + ", startPos was: " + startPos);
        }
        long val = ((0xFFL & arr[startPos + 0]) << 56) //
                | ((0xFFL & arr[startPos + 1]) << 48) //
                | ((0xFFL & arr[startPos + 2]) << 40) //
                | ((0xFFL & arr[startPos + 3]) << 32) //
                | ((0xFFL & arr[startPos + 4]) << 24) //
                | ((0xFFL & arr[startPos + 5]) << 16) //
                | ((0xFFL & arr[startPos + 6]) << 8) //
                | (0xFFL & arr[startPos + 7]);
        return val;
    }
```
```java
    static void longToArray(long val, byte[] arr, int startPos) {
        if (startPos < 0) {
            throw new IllegalArgumentException("startPos must not be negative. was: " + startPos);
        }
        if ((arr.length - startPos) < 8) {
            throw new IllegalArgumentException("Array has to have at least 8 bytes after startPos. arr.length was: " + arr.length + ", startPos was: " + startPos);
        }
        arr[startPos + 0] = (byte) (val >>> 56);
        arr[startPos + 1] = (byte) (val >>> 48);
        arr[startPos + 2] = (byte) (val >>> 40);
        arr[startPos + 3] = (byte) (val >>> 32);
        arr[startPos + 4] = (byte) (val >>> 24);
        arr[startPos + 5] = (byte) (val >>> 16);
        arr[startPos + 6] = (byte) (val >>> 8);
        arr[startPos + 7] = (byte) val;
    }
```
