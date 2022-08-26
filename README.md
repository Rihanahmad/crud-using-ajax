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


