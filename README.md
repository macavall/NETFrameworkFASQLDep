# NETFrameworkFASQLDep
---  
        Timer Trigger Function App making outbound SQL Query  
        Will need the connection string to complete in the ```App Settings```

```C#
        private static void ReadOrderData(string connectionString, ILogger log)
        {
            string queryString =
                "SELECT Id, ColOne FROM dbo.testtable56;";
            using (SqlConnection connection = new SqlConnection(
                       connectionString))
            {
                SqlCommand command = new SqlCommand(
                    queryString, connection);
                connection.Open();
                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        log.LogInformation(String.Format("{0}, {1}",
                            reader[0], reader[1]));
                    }
                }
            }
        }
    }
```
