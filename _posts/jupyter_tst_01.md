
```pythonimport sys; sys.path.append(r'W:\A\AMS\Team\WISE\py_scripts')import qad```
```pythondf = qad.get_new_listings()df```
    ---------------------------------------------------------------------------
    ProgrammingError                          Traceback (most recent call last)
    C:\Python\winpython_3_5_2_1\python-3.5.2.amd64\lib\site-packages\pandas\io\sql.py in execute(self, *args, **kwargs)       1563             else:    -> 1564                 cur.execute(*args)       1565             return cur    
    ProgrammingError: ('42000', "[42000] [Microsoft][ODBC SQL Server Driver][SQL Server]Unclosed quotation mark after the character string '\n    '. (105) (SQLExecDirectW)")
        During handling of the above exception, another exception occurred:    
    DatabaseError                             Traceback (most recent call last)
    <ipython-input-2-7057ec2f706b> in <module>()    ----> 1 df = qad.get_new_listings()          2 df    
    W:\A\AMS\Team\WISE\py_scripts\qad.py in get_new_listings(as_of_date)         48          49     cnxn = jss.sql_cnxn('qad')    ---> 50     df = pd.read_sql(sql, cnxn)         51          52     return df    
    C:\Python\winpython_3_5_2_1\python-3.5.2.amd64\lib\site-packages\pandas\io\sql.py in read_sql(sql, con, index_col, coerce_float, params, parse_dates, columns, chunksize)        497             sql, index_col=index_col, params=params,        498             coerce_float=coerce_float, parse_dates=parse_dates,    --> 499             chunksize=chunksize)        500         501     try:    
    C:\Python\winpython_3_5_2_1\python-3.5.2.amd64\lib\site-packages\pandas\io\sql.py in read_query(self, sql, index_col, coerce_float, params, parse_dates, chunksize)       1597        1598         args = _convert_params(sql, params)    -> 1599         cursor = self.execute(*args)       1600         columns = [col_desc[0] for col_desc in cursor.description]       1601     
    C:\Python\winpython_3_5_2_1\python-3.5.2.amd64\lib\site-packages\pandas\io\sql.py in execute(self, *args, **kwargs)       1574             ex = DatabaseError(       1575                 "Execution failed on sql '%s': %s" % (args[0], exc))    -> 1576             raise_with_traceback(ex)       1577        1578     @staticmethod    
    C:\Python\winpython_3_5_2_1\python-3.5.2.amd64\lib\site-packages\pandas\compat\__init__.py in raise_with_traceback(exc, traceback)        331         if traceback == Ellipsis:        332             _, _, traceback = sys.exc_info()    --> 333         raise exc.with_traceback(traceback)        334 else:        335     # this version of raise is a syntax error in Python 3    
    C:\Python\winpython_3_5_2_1\python-3.5.2.amd64\lib\site-packages\pandas\io\sql.py in execute(self, *args, **kwargs)       1562                 cur.execute(*args, **kwargs)       1563             else:    -> 1564                 cur.execute(*args)       1565             return cur       1566         except Exception as exc:    
    DatabaseError: Execution failed on sql '        select eqi.InfoCode,          IsPrimExchQt,          MIC,          MICDesc,          ExchName,          ExchCtryCode,          x.Open_,          x.High,          x.Low,          x.Close_,          x.Volume,          x.Bid,          x.Ask,          x.VWAP,          x.MostTrdPrc,          x.ConsolVol,          x.MostTrdVol        from DS2ExchQtInfo eqi        join DS2Exchange e        on eqi.ExchIntCode = e.ExchIntCode        join        (        select * from DS2ScdQtPrc        union        select * from DS2PrimQtPrc        ) x        on eqi.InfoCode = x.InfoCode and         eqi.ExchIntCode = x.ExchIntCode        where StartDate = 20170509'        ': ('42000', "[42000] [Microsoft][ODBC SQL Server Driver][SQL Server]Unclosed quotation mark after the character string '\n    '. (105) (SQLExecDirectW)")

```python
```
