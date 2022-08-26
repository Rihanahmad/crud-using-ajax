# crud-using-ajax
//$(document).ready(function () {
//    $.ajax({
//        type: "GET",
//        url: "/Home/getcountry",
//        data: "{}",
//        success: function (data) {
//            var s = '<option value="-1">Please Select a country</option>';
//            for (var i = 0; i < data.length; i++) {
//                s += '<option value="' + data[i].id+ '">' + data[i].name + '</option>';
//            }
//            $("#dropdown").html(s);
//        }
//    });
//});  



//public JsonResult getCountry(countrytab userModal1)
        //{
        //    string r = string.Empty;
        //    SqlConnection con = new SqlConnection(WebConfigurationManager.AppSettings["DBCon"].ToString());
        //    con.Open();
        //    SqlCommand com = new SqlCommand("CRUDUsers", con);
        //    SqlParameter[] sp = new SqlParameter[3];
        //    sp[0] = new SqlParameter("@id", userModal1.id);
        //    sp[1] = new SqlParameter("@name", userModal1.name);
        //    sp[2] = new SqlParameter("@ActionType", userModal1.ActionType);


        //    com.CommandType = CommandType.StoredProcedure;
        //    com.Parameters.AddRange(sp);
        //    DataTable dt = new DataTable();
        //    SqlDataAdapter sqda = new SqlDataAdapter(com);
        //    sqda.Fill(dt);
        //    con.Close();
        //    if (userModal1.ActionType == "get")
        //    {
        //        return Json(dt.Rows[0]["MS"].ToString(), JsonRequestBehavior.AllowGet);
        //    }

        //    else
        //    {
        //        List<countrytab> ObjEmp = new List<countrytab>();
        //        for (int i = 0; i < dt.Rows.Count; i++)
        //        {
        //            countrytab userModal = new countrytab();
        //            userModal1.id = Convert.ToInt32(dt.Rows[i]["id"].ToString());
        //            userModal1.name = dt.Rows[i]["name"].ToString();

        //            ObjEmp.Add(userModal1);
                   
        //        }
        //        return Json(ObjEmp, JsonRequestBehavior.AllowGet);



        //    }
        //}

    public int id { get; set; }
        public string name { get; set; }
        public string ActionType { get; set; }


sql.................




Alter procedure CRUDUsers
@Id int=null,
@Name nvarchar(100)=null,
@Age nvarchar(100)=null,
@Gender nvarchar(100)=null,
@Email nvarchar(100)=null,
@Address nvarchar(100)=null,
@Country nvarchar(100)=null,
@ActionType nvarchar(100)
AS
Begin
IF @ActionType='Insert'
Begin
if Exists(select * from username where name=@Name)
Begin
	Select 0 as 'Success', 'Record already exisits' as 'MSG'
End
else if Exists(select * from username where email=@Email)
Begin
	Select 0 as 'Success', 'Record already exisits' as 'MSG'
End

Else
Begin
Insert into username(name,age,gender,email,[address],country)
Values(@Name,@Age,@Gender,@Email,@Address,@Country)

Select 1 as 'Success', 'Record has been inserted successfully' as 'MSG'
ENd

END
ELSE IF @ActionType='getALL'
Begin
Select * from username
END

ELSE IF @ActionType='Update'
Begin
update username set name=@Name, age=@Age,gender=@Gender,email=@Email,address=@address,country=@Country where id=@id
Select 1 as 'Success', 'Record has been updated successfully' as 'MSG'
END

else if @ActionType='Delete'
begin
delete from username where id=@id
Select 1 as 'Success', 'Record has been deleted successfully' as 'MSG'
end
else if @ActionType='FillById'
begin
select * from username  where id=@id
end

else if @ActionType='get'
begin
select id, name from countrytab 
end


else if @ActionType='getcountry' 


begin
 DECLARE @countryid INT
select id,name,countryid from statetab where countryid=@countryid
end
End









