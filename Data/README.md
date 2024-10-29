# How to access the data: 
1. Install pymongo library
2. Import the library in your Python script or Jupyter Notebook
3. Database Access Credentials: Establish a connection to the MongoDB server using the MongoClient through this connection string, including a username (user) and password (123):
    - client = MongoClient("mongodb+srv://user:123@cluster0.9d0ja.mongodb.net/?       retryWrites=true&w=majority&appName=Cluster0")
4. To access the blancco database, use the following code:
    - db = client["blancco"]
5. Within the blancco database, you can access the all_reports collection as shown below:
    - all_reports_collection = db["all_reports"]
6. Performing Operations: You can now use the all_reports_collection to perform various operations such as finding, inserting, updating, or aggregating data
