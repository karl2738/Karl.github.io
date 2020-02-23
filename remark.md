## 数据集：
https://grouplens.org/datasets/movielens/

MovieLens 1M数据集
MovieLens 1M 电影分级。 稳定的基准数据集。6000个用户观看4000部电影时获得1百万个评分。发布2/2003。

本项目使用的是MovieLens 1M 数据集，包含6040个用户在近3883部电影上的100w条评论。
数据集分为三个文件：用户数据users.dat，电影数据movies.dat和评分数据ratings.dat。
## 用户数据
分别有用户ID、性别、年龄、职业ID和邮编等字段。
数据中的格式：UserID::Gender::Age::Occupation::Zip-code
 UserID Gender Age OccupationID Zip-code
0 1 F 1 10 48067
1 2 M 56 16 70072
2 3 M 25 15 55117
3 4 M 45 7 02460
4 5 M 25 20 55455
## 电影数据
分别有电影ID、电影名和电影风格等字段。
数据中的格式：MovieID::Title::Genres
 MovieID Title Genres
0 1 Toy Story (1995) Animation|Children's|Comedy
1 2 Jumanji (1995) Adventure|Children's|Fantasy
2 3 Grumpier Old Men (1995) Comedy|Romance
3 4 Waiting to Exhale (1995) Comedy|Drama
4 5 Father of the Bride Part II (1995) Comedy
## 评分数据
分别有用户ID、电影ID、评分和时间戳等字段。
数据中的格式：UserID::MovieID::Rating::Timestamp
 UserID MovieID Rating timestamps
0 1 1193 5 978300760
1 1 661 3 978302109
2 1 914 3 978301968
3 1 3408 4 978300275
4 1 2355 5 978824291
评分字段Rating就是我们要学习的targets，时间戳字段我们不使用。
## 数据预处理
UserID、Occupation和MovieID不用变。
Gender字段：需要将‘F’和‘M’转换成0和1。
Age字段：要转成7个连续数字0~6。
Genres字段：是分类字段，要转成数字。首先将Genres中的类别转成字符串到数字的字典，然后再将每个电影的Genres字段转成数字列表，因为有些电影是多个Genres的组合。
Title字段：处理方式跟Genres字段一样，首先创建文本到数字的字典，然后将Title中的描述转成数字的列表。另外Title中的年份也需要去掉。需要去除括号
Genres和Title字段需要将长度统一，这样在神经网络中方便处理。空白部分用‘< PAD >’对应的数字填充。

MovieLens 25M数据集
MovieLens 20M 电影分级。 稳定的基准数据集。2000万个分级和465,000个标签应用程序由138,000个用户应用于27,000部电影。包括在1,129个标签中具有1500万相关分数的标签基因组数据。已发行12/2019

## 电影数据
电影信息包含在文件中movies.csv。标题行之后的此文件的每一行代表一部电影，并具有以下格式：
movieId,title,genres
movieId imdbId tmdbId
1 114709 862
2 113497 8844
3 113228 15602

## 评分数据
userId movieId rating timestamp
1 296 5 1147880044
1 306 3.5 1147868817
1 307 5 1147868828
1 665 5 1147878820

无用户数据（性别，职位，年龄），不太好
其他比较新的数据集也是如此，都没有用户数据

