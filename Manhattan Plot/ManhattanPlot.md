Manhattan plot
================
Li-Hsin Chien
2025-04-11

使用 package: *qqman*

指令 *manhattan* 需要輸入的資料包含:

- chr: 染色體編號
- bp: 染色體上的位置 (basepair)
- snp: SNP id
- p: GWAS p-value

以上這些， plink 指令 –linear 產生的 output 都有。

讀入範例檔案: *Manhattan_test.assoc.linear*:

``` r
r<-read.table(file="Manhattan_test.assoc.linear",header=T)
head(r,12)
```

    ##    CHR         SNP    BP A1 TEST NMISS     BETA     STAT         P
    ## 1    1 rs180734498 13302  T  ADD  1092  -0.3088  -0.9515 3.416e-01
    ## 2    1 rs180734498 13302  T  sex  1092   4.7970  18.7600 3.062e-68
    ## 3    1 rs180734498 13302  T  pc1  1092 -47.4100 -10.8000 7.012e-26
    ## 4    1 rs180734498 13302  T  pc2  1092   1.4740   0.3434 7.313e-01
    ## 5    1 rs180734498 13302  T  pc3  1092  -2.1200  -0.4810 6.306e-01
    ## 6    1 rs141149254 54490  A  ADD  1092   0.4695   1.3760 1.690e-01
    ## 7    1 rs141149254 54490  A  sex  1092   4.7880  18.7300 4.917e-68
    ## 8    1 rs141149254 54490  A  pc1  1092 -47.0100 -11.0500 5.641e-27
    ## 9    1 rs141149254 54490  A  pc2  1092   4.1690   0.9367 3.491e-01
    ## 10   1 rs141149254 54490  A  pc3  1092  -0.7597  -0.1800 8.572e-01
    ## 11   1  rs10399749 55299  T  ADD  1092  -0.1092  -0.4890 6.250e-01
    ## 12   1  rs10399749 55299  T  sex  1092   4.7950  18.7400 4.285e-68

``` r
m<-dim(r)[1]/5 # SNP 個數
r.snp<-r[5*(1:m)-4,]

manhattan(r.snp,chr="CHR",bp="BP",snp="SNP",p="P",suggestiveline=F,annotatePval = 5*10^-8)
```

![](ManhattanPlot_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

PS: 這個範例由於要縮小檔案大小的關係，有刪減 SNPs。你們跑的時候因為 SNPs
個數多非常多，出圖的時間可能會比較久。

Reference: <https://r-graph-gallery.com/101_Manhattan_plot.html>
