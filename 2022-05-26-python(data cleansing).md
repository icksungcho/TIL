Let's say this is an original code;

    def check_range(dfs):

       df_mask = df.isna()
       df_filled = df.mask(df_mask, 0.5)
       gte0 = df_filled >= 0.0
       lte1 = df_filled <= 1.0

       return gte0.all(axis=None) and lte1.all(axis=None)

  
We can change it with data cleansing;

    def check_range(dfs):

       lbound = 0.0
       ubound = 1.0
       df_mask = dfs.isna()
       df_filled = dfs.mask(df_mask, mean([lbound,ubound])
       in_lbound = (dfs.filled >=lbound).all(axis=None)
       in_ubound = (dfs.filled <=ubound).all(axis=None)

       return in_lbound and in_ubound
        
 Seems like more intuitive than before
