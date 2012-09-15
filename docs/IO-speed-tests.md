```r
zz =rmr2:::interleave(1:10^6, 1:10^6)
con = file("/tmp/nwtest", "wb")
> system.time({rmr2:::native.writer(zz, con)})
user  system elapsed 
56.864   4.599  61.481 
> system.time({save(zz, file= "/tmp/save-test")})
user  system elapsed 
1.535   0.010   1.546 
> system.time({writeBin(rmr2:::typed.bytes.writer(objects=zz), con=file("/tmp/tb-test", "wb"))})
user  system elapsed 
0.312   0.038   0.350 
> system.time({rmr2:::make.typed.bytes.input.format()(file("/tmp/nwtest", "rb"), 10^5)})
user  system elapsed 
4.169   0.158   4.336 
> system.time({load(file="/tmp/save-test")})
user  system elapsed 
0.645   0.009   0.659 
> system.time({rmr2:::make.typed.bytes.input.format()(file("/tmp/tb-test", "rb"), 10^6)})
user  system elapsed 
2.215   0.162   2.376 
```
