component {
    function run(){
        var data = {folderName:"",password:""}
        if(fileExists(expandpath(getCwd() & "\student.json"))){
            data = deserializeJSON(fileRead(expandPath(getCwd() & "\student.json" )))
        }
        var envFile = fileRead(".env.example");
        var folderName = listlast(getCwd(),"/\");
        fileWrite(".env",envFile.replace("USERNAMEHERE",folderName,"all").replace("PASSWORDHERE",data.password,"all"))

        if(fileExists(expandpath(getCwd() & "\.cfconfig.json"))){
            var cfconfig = fileRead(expandpath(getCwd() & "\.cfconfig.json"));
            fileWrite(expandpath(getCwd() & "\.cfconfig.json"), cfconfig.replace("**DSOURCENAME**",folderName,"all"));
        }
        var applicationCFC = fileRead(expandpath(getCwd() & "\Application.cfc"));
        fileWrite(expandpath(getCwd() & "\Application.cfc"), applicationCFC.replace("USERNAMEHERE",folderName,"all"));

        try{
        fileMove(".cfconfig.json","../.cfconfig.json");
        fileMove(".env","../.env");
        } catch(any err){
            
        }
    }
}