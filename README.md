# Water-Meter-Number-DataSet

The Water Meter Number DataSet for the research of Water Meter Number Recognition is released by Deep Leaning and Visual Computing Lab of South China University of Technology.

The dataset would be available soon.

**Note: The Water Meter Number DataSet can only be used for non-commercial research purpose.**

## Description
The Water Meter Number DataSet consists of two parts. The first part contains 5000 noisy samples (as shown in Fig. 1a). Within the noisy samples, there is a wide range of variation caused by illumination, refraction, occlusion, etc. The second part contains 1000 clean samples (as shown in Fig. 1b). Both the noisy and clean samples are labeled with sequential characters like “1; 2; 2; 5; 8”.

![Figure 1](https://github.com/jiarenyf/Water-Meter-Number-DataSet/raw/master/imgs/fig1.png)

The number of each character in the dataset is shown in Table 1.

![Table 1](https://github.com/jiarenyf/Water-Meter-Number-DataSet/raw/master/imgs/table1.png)

In Water Meter Number Recognition, there exist some “mid-state” characters, as shown in Fig. 2. Taking the 4th image (row 2, column 1) in Fig. 2b as an example, the number exceeds “20369” but does not reach “20370”, so that the last two characters in the number appear at the “mid-state”. And the proper watermeter number should be “20369.5”.

![Figure 2](https://github.com/jiarenyf/Water-Meter-Number-DataSet/raw/master/imgs/fig2.png)

To manage “mid-state” characters, we treat the “mid-state" characters as separate classes, with labels ranging from '10' to '19', as shown in Fig. 3.

![Figure 3](https://github.com/jiarenyf/Water-Meter-Number-DataSet/raw/master/imgs/fig3.png)

A label l in [10, 19], denotes a character that exceeds “l − 10” (called the “lower-state”) but does not reach “l − 9” (called the “higher-state”). As a special case, label “l = 19” indicates that the character is at “mid-state” between ‘9’ and ‘0’ (ignoring carry). In such setting, the label for the 4th image in Fig. 2b is “2; 0; 3; 16; 19”. This label sequence could be further processed to the water-meter number “20369.5” as shown in Equation (1):

![Equation 1](https://github.com/jiarenyf/Water-Meter-Number-DataSet/raw/master/imgs/equation1.png)

If the predicted digit is at the end of the sequence, and is at “mid-state”, we subtract the digit by 9.5. For example, a predicted result 12, which means that the corresponding number exceeds 2 but does not reach 3, we choose to predict it as 2 and append a “mid-state” flag to the result by adding the final number with 0.5. If the “midstate” character is not the last one, then we simply subtract the digit by 10, saying the “lower-state” is selected, which is intuitively more reasonable.

## Citation and Contact
For any quetions about the dataset, please contact the authors by sending email to yfjiaren@foxmail.com and eelwjin@scut.edu.cn.

## Acknowledgement
This research is supported in part by GD-NSF (no.2017A030312006), the National Key Research and Development Program of China (No. 2016YFB1001405), NSFC (Grant No.: 61472144, 61673182, 61771199), GDSTP (Grant No.: 2017A010101027).

