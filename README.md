This is an updated copy of the [ROB](https://en.wikipedia.org/wiki/Re-order_buffer) size testing tool described by [Henry Wong on his blog](http://blog.stuffedcow.net/2013/05/measuring-rob-capacity). It includes one additional test (test 26) which uses AVX-512 `zmm` registers, and hence can measure the size of the 512-bit register file (spoiler: it seems to be the same size as the `ymm` and `xmm` register file, so nothing tricky going on).

Build it with `make` and run it like `./robsize N` where N is a test number from 0 to 26 (for now see `test_name` in the source to determine which tests are which).

There are a few options that you can see with `./robsize -help`:

```
Usage: 	robsize [TEST_NUMBER] [OPTIONS]

	-slow			Run more iterations making the test slower but potentiallly more accurate
	-fast			Run fewer iterations making the test faster but potentiallly less accurate
	-write-asm			Print the raw generated instructions to a file and quit
```

### References

H. Wong, _Measuring Reorder Buffer Capacity_, May, 2013. [Online]. Available: http://blog.stuffedcow.net/2013/05/measuring-rob-capacity/