1. Broadcast joins - One large and one small table join scenarios

![image](https://user-images.githubusercontent.com/53032061/113486399-1caadc00-94d0-11eb-86ec-755d3f91087f.png)

![image](https://user-images.githubusercontent.com/53032061/113488430-baf06f00-94db-11eb-949a-aff03cf0df1f.png)

![image](https://user-images.githubusercontent.com/53032061/113486346-d5245000-94cf-11eb-9e2c-ddbf3a33d089.png)


2. Technique 2: Column Pruning

Though Spark tries to do column pruning as much as possible, it does not achieve that every time. So, best practice is to pick only those columns in your dataframes which are actually needed in the output dataframe. This can be done by doing Select of only the needed columns BEFORE the join.

3. Technique 3: Push operations to the map side, if possible. This is especially application in case of outer joins where output DF is much larger than source DF (on which the operation is being done). What it means is that instead of applying an operation after the join on the final DF, apply that operation on the source DF field before the join and use that field for the output.

e.g. If you have to apply an Upper function on field1 of target DF and the source of this field in SourceDF1, instead of joining SourceDF1, apply this Upper function to create SourceDF2 and then use it to join with other dataframes

4. Technique 4: Partitioning Tips

![image](https://user-images.githubusercontent.com/53032061/113518440-02423280-95a4-11eb-91db-d267cc22984c.png)



5. Technique 5: Bucketing

![Uploading image.png…]()
