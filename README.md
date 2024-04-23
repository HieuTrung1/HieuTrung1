_G.kick = false
local Pedo = {
    1135910299, -- Havelic
    1619950875, -- Pixel_SkillzSPIN2
    1581720092, -- Pixel_SkillzSPIN
    1661505948, -- Pixel_SkillzBARRIER
    679804290, -- Pixel_Skillz
    520944, -- Oblivic
    43247021, -- BowTiedPony
    2350183594, -- icydragonwingsis
    1338963426, -- happypandamagic2
    1276541545, -- VanitasThePlague
    587649463, -- happypandamagic
    245586741, -- Tiptop98
    174941504, -- FoxKingFab
    136099207,-- CudlessTheCat
    94825741, -- NATSUDRAGN331
    358051152, -- VortexFragmented
    529455640, -- vlonedd
    281482099, -- Quixotize
    355207559, -- Elianmc1s
    5084487, -- Americanflag
    928623624, -- TrashPanda2361
    30049170, -- Farquanetta
    474452017 -- Bige0n
    }

for _, v in pairs(game:GetService("Players"):GetPlayers()) do
    for _, v1 in pairs(Pedo) do
        if v.UserId == v1 then
            game:GetService("Players").LocalPlayer:Kick("Admin is in the server")
        end
    end
end

game:GetService("Players").PlayerAdded:Connect(function(r)
    for _, v in pairs(Pedo) do
        if r.UserId == v then
            game:GetService("Players").LocalPlayer:Kick("Admin or Staff has joined the server")
        end
    end
end)

local vu = game:GetService("VirtualUser")
game:GetService("Players").LocalPlayer.Idled:connect(function()
vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
wait(1)
vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)


local Players = game:GetService("Players")
local cache = {}
function lol(name)
    if cache[name] then return cache[name] end
    local player = Players:FindFirstChild(name)
    if player then
        cache[name] = player.UserId
    return player.UserId
end 


local id
pcall(function ()
    id = Players:lol(name)
end)
cache[name] = id
return id
end
local ehh = game.Players.LocalPlayer.Name
local Final = lol(ehh)
getgenv().firstfruit = game.Workspace.UserData["User_"..Final].Data["DevilFruit"].Value
getgenv().secondfruit = game.Workspace.UserData["User_"..Final].Data["DevilFruit2"].Value

do  
local fishingplace =  game:GetService("Workspace"):FindFirstChild("fishingplace")  
if fishingplace then 
fishingplace:Destroy() 
end 
end
local fishingplace = Instance.new("Part",game.Workspace)
fishingplace.Name = "fishingplace"
fishingplace.Size = Vector3.new(2,1,2)
fishingplace.Position = Vector3.new(19784, 210,5000)
fishingplace.Anchored = true

do  
local safezonedestroyspace =  game:GetService("Workspace"):FindFirstChild("SafeZoneOuterSpacePart")  
if safezonedestroyspace then 
safezonedestroyspace:Destroy() 
end 
end
local SafeZoneOuterSpace = Instance.new("Part",game.Workspace)
SafeZoneOuterSpace.Name = "SafeZoneOuterSpacePart"
SafeZoneOuterSpace.Size = Vector3.new(200,3,200)
SafeZoneOuterSpace.Position = Vector3.new((math.random(-100000, 100000)), 10000, (math.random(-100000, 100000)))
SafeZoneOuterSpace.Anchored = true

local mta = getrawmetatable(game)
local namecall = mta.__namecall
local setreadonly = setreadonly or make_writable


setreadonly(mta, false)

mta.__namecall = newcclosure(function(self, ...)
    local args = {...}
    local arguments = args
    local a = {}
    for i = 1, #arguments - 1 do
        a[i] = arguments[i]
    end
    local method = getnamecallmethod() 

    if method == 'FireServer' or method == "InvokeServer" then
        if self.Name == 'Drown' and _G.nowaterdamage then
            if args[1] then
                return nil
            end
        end
    end
    
    return namecall(self, ...)    
end)

local attackremote = {}    

local a
a=hookmetamethod(game,"__namecall",function(self,...)
    local args = {...}
    local method = getnamecallmethod()
    if method == "FireServer" or method == "InvokeServer" then
        if self.Name == "RequestAnimation" and game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 then
            attackremote[self.Name] = args[1]
            return a(self,unpack(args))
        elseif self.Name == "RequestAnimation" and game.Players.LocalPlayer.Character.Humanoid.Health == 0 then
            attackremote[self.Name] = ""
        end
    end
      return a(self,...)
end)

aaxc = hookmetamethod(game, "__namecall", function(self, ...)
    local args = {...}
    local method = getnamecallmethod()
    if method == "FireServer" or method == "InvokeServer" then
        if self.Name == "RemoteEvent" and args[3] == "StopCharging" and _G.auto100rate then
            args[6] = 100
            return aaxc(self, unpack(args))
        end
    end
    return aaxc(self, ...)
end)

local remotes = {}
    local azc
    azc=hookmetamethod(game,"__namecall",function(self,...)
        local args = {...}
        local method = getnamecallmethod()
        if method == "FireServer" or method == "InvokeServer" then
            if self.Name == "RemoteEvent" and args[3] == "StopCharging" or args[3] == "Create" then
                remotes[self.Name] = args[1]
                return azc(self,unpack(args))
            end
        end
          return azc(self,...)
    end)
    
    function serializeTable(val, name, skipnewlines, depth)
    skipnewlines = skipnewlines or false
    depth = depth or 0
 
    local tmp = string.rep("", depth)
 
    if name then tmp = tmp end
 
    if type(val) == "table" then
        tmp = tmp .. (not skipnewlines and "" or "")
 
        for k, v in pairs(val) do
            tmp =  tmp .. serializeTable(v, k, skipnewlines, depth + 1) .. (not skipnewlines and "" or "")
        end
 
        tmp = tmp .. string.rep("", depth) 
    elseif type(val) == "number" then
        tmp = tmp .. tostring(val)
    elseif type(val) == "string" then
        tmp = tmp .. string.format("%q", val)
    elseif type(val) == "boolean" then
        tmp = tmp .. (val and "true" or "false")
    elseif type(val) == "function" then
        tmp = tmp  .. "func: " .. debug.getinfo(val).name
    else
        tmp = tmp .. tostring(val)
    end
    return tmp
end
local plr = game.Players.LocalPlayer.Character.Name

local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "Nothing Hub",
    SubTitle = "by Nothing xD",
    TabWidth = 160,
    Size = UDim2.fromOffset(520, 360),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

Fluent:Notify({
    Title = "Nothing",
    Content = "Loading . . .",
    Duration = 3
})
wait(2)

local Tab2 = {Main = Window:AddTab({ Title = "Farming"}),}
wait(0.2)
local Tab3 = {Main = Window:AddTab({ Title = "ISLAND/TELEPORT"}),}
wait(0.2)
local Tab9 = {Main = Window:AddTab({ Title = "KILL/DEF FARM"}),}
wait(0.2)
local Tab4 = {Main = Window:AddTab({ Title = "SHOP"}),}
wait(0.2)
local Tab5 = {Main = Window:AddTab({ Title = "PLAYER"}),}
wait(0.2)
local Tab7 = {Main = Window:AddTab({ Title = "MOB BRING"}),}
wait(0.2)
local Tab6 = {Main = Window:AddTab({ Title = "AUTO SKILL"}),}
wait(0.2)
local Tab1 = {Main = Window:AddTab({ Title = "MISC"}),}
wait(0.2)
local Tab8 = {Main = Window:AddTab({ Title = "SETTING"}),}

Weapon = {}
        function FindWeapon()
            for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
                if v:IsA("Tool") then
                   table.insert(Weapon, v.Name)
                end
             end
        end
    
        setfflag("HumanoidParallelRemoveNoPhysics", "False")
        setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
        
        function EquipWeapon(ToolSe)
            if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
                local tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
                wait(.1)
                game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
            end
        end
        function Skill(use)
            game:GetService("VirtualInputManager"):SendKeyEvent(true,use,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
            wait(.1)
            game:GetService("VirtualInputManager"):SendKeyEvent(false,use,false,game.Players.LocalPlayer.Character.HumanoidRootPart)
        end
        if not game:GetService("Workspace"):FindFirstChild("LOL") then
            local LOL = Instance.new("Part")
            LOL.Name = "LOL"
            LOL.Parent = game.Workspace
            LOL.Anchored = true
            LOL.Transparency = 0
            LOL.Size = Vector3.new(50,0.5,50)
            game.Workspace["LOL"].CFrame = CFrame.new(0,50000,0)
        end
        Wapon = {}
        for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
            if v:IsA("Tool") then
                table.insert(Wapon ,v.Name)
            end
        end
        for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
            if v:IsA("Tool") then
                table.insert(Wapon, v.Name)
            end
        end
print('ss')
Tab9.Main:AddParagraph({
    Title = "Nothing",
    Content = "┇ WEAPON SPAM (YORU FOR DEF FARMING) ┇"
})
Speeds = 50

local Slider = Tab9.Main:AddSlider("Slider", {
    Title = "Yoru Speed",
    Description = "Change Yoru Attack Speed",
    Default = 50,
    Min = 0,
    Max = 200,
    Rounding = 1,
    Callback = function(to)
        Speeds = to
    end
})

local FYoru = Tab9.Main:AddToggle("Fast yoru", {Title = "Fast Atk Yoru", Default = false })

FYoru:OnChanged(function(yoru)
    _G.Yoru = yoru
    if _G.Yoru then
        print("Fast Atk Yoru On")
    end
while _G.Yoru do
    
wait()
    local Players = game:GetService("Players")
    local Plr = Players.LocalPlayer
    local Character = Plr.Character
    local Yoru = Character:FindFirstChild("Yoru")
    local Environment
wait()
pcall(function()
for i,v in pairs(getconnections(Yoru["RequestAnimation"].OnClientEvent)) do 
    Environment = getsenv(Yoru["AnimationController"])
end
    wait()
for i = 1, Speeds do
Yoru["RequestAnimation"]:FireServer(Environment.PlaceId)
end
end)
wait()
end
end)

Speedss = 50
local Slider2 = Tab9.Main:AddSlider("Slider", {
    Title = "Cestus Speed",
    Description = "Change Cestus Attack Speed",
    Default = 50,
    Min = 0,
    Max = 200,
    Rounding = 1,
    Callback = function(too)
        Speeds = too
    end
})

local Cestus = Tab9.Main:AddToggle("MyToggle", {Title = "Cestus Fast Atk", Default = false })

Cestus:OnChanged(function(seastone)
    _G.Cestus = seastone
    if _G.Cestus then
        print("speedCestus On")
    end
while _G.Cestus do
wait()
    local Players = game:GetService("Players")
    local Plr = Players.LocalPlayer
    local Character = Plr.Character
    local Cestus = Character:FindFirstChild("Seastone Cestus")
    local Environment
wait()
pcall(function()
for i,v in pairs(getconnections(Cestus["RequestAnimation"].OnClientEvent)) do 
    Environment = getsenv(Cestus["AnimationController"])
end
    wait()
for i = 1, Speedss do
Cestus["RequestAnimation"]:FireServer(Environment.PlaceId)
end
end)
end
end)

Tab9.Main:AddParagraph({
    Title = "Quake Farm",
    Content = "Auto Farming With Quake Fruit(Far Distance)"
})

local QuakeFarm = Tab9.Main:AddToggle("MyToggle", {Title = "Quake Auto Farm", Default = false })

QuakeFarm:OnChanged(function(quakefarm)
    getgenv().quakefarm1 = quakefarm
        while getgenv().quakefarm1 do wait()
    pcall(function()
local x = getsenv(game:GetService("Players").LocalPlayer.Character.Powers.Quake)
local v = x.VTCebvc
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1848.4346923828125, 222, -450.0833740234375), Vector3.new(-0.5347824096679688, -0.43560168147087097, -0.7240573167800903)),100,Vector3.new(-1848.4346923828125, 222, -450.0833740234375), Vector3.new(-0.5347824096679688, -0.43560168147087097, -0.7240573167800903))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1898.96728515625, 225.03367614746094, -200.6829071044922), Vector3.new(-0.9484627842903137, -0.18392488360404968, 0.25805023312568665)),100,Vector3.new(-1898.96728515625, 225.03367614746094, -200.6829071044922), Vector3.new(-0.9484627842903137, -0.18392488360404968, 0.25805023312568665))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1749.58203125, 224.88922119140625, -134.49240112304688), Vector3.new(-0.6882264614105225, -0.40487319231033325, 0.6020150184631348)),100,Vector3.new(-1749.58203125, 224.88922119140625, -134.49240112304688), Vector3.new(-0.6882264614105225, -0.40487319231033325, 0.6020150184631348))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1622.5482177734375, 225.85337829589844, -200.26828002929688), Vector3.new(-0.3189719319343567, -0.7127735018730164, 0.6246685981750488)),100,Vector3.new(-1622.5482177734375, 225.85337829589844, -200.26828002929688), Vector3.new(-0.3189719319343567, -0.7127735018730164, 0.6246685981750488))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(1002.1565551757812, 214, 3349.3857421875), Vector3.new(-0.2978745698928833, -0.6442758440971375, 0.7044001221656799)),100,Vector3.new(1002.1565551757812, 214, 3349.3857421875), Vector3.new(-0.2978745698928833, -0.6442758440971375, 0.7044001221656799))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(2167.46923828125, 213, -631.9636840820312), Vector3.new(0.6589730978012085, -0.6376858949661255, -0.3988874852657318)),100,Vector3.new(2167.46923828125, 213, -631.9636840820312), Vector3.new(0.6589730978012085, -0.6376858949661255, -0.3988874852657318))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(1178.6993408203125, 212.26193237304688, -263.04681396484375), Vector3.new(0.04516664147377014, -0.9571055173873901, 0.28619781136512756)),100,Vector3.new(1178.6993408203125, 212.26193237304688, -263.04681396484375), Vector3.new(0.04516664147377014, -0.9571055173873901, 0.28619781136512756))
wait(0.1)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1040.117919921875, 215, 1662.1202392578125), Vector3.new(0.9582481980323792, -0.13812202215194702, 0.2503652274608612)), 100,Vector3.new(-1040.117919921875, 215, 1662.1202392578125), Vector3.new(0.9582481980323792, -0.13812202215194702, 0.2503652274608612))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-988.4560546875, 283, 1616.5068359375), Vector3.new(-0.44781866669654846, -0.36267393827438354, 0.8172675371170044)), 100,Vector3.new(-988.4560546875, 283, 1616.5068359375), Vector3.new(-0.44781866669654846, -0.36267393827438354, 0.8172675371170044))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1037.58544921875, 215.7229461669922, 1508.449951171875), Vector3.new(-0.7139230966567993, -0.5779988169670105, 0.39526084065437317)),100,Vector3.new(-1037.58544921875, 215.7229461669922, 1508.449951171875), Vector3.new(-0.7139230966567993, -0.5779988169670105, 0.39526084065437317))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-908.2176513671875, 214, 1621.364990234375), Vector3.new(-0.21460314095020294, -0.40479180216789246, 0.88886958360672)),100,Vector3.new(-908.2176513671875, 214, 1621.364990234375), Vector3.new(-0.21460314095020294, -0.40479180216789246, 0.88886958360672))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-248.8604736328125, 273.4266052246094, 355.64453125), Vector3.new(0.6645273566246033, -0.5016912817955017, -0.5538134574890137)),100,Vector3.new(-248.8604736328125, 273.4266052246094, 355.64453125), Vector3.new(0.6645273566246033, -0.5016912817955017, -0.5538134574890137))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-319.3795471191406, 272.3931884765625, 388.7362060546875), Vector3.new(0.5347911715507507, -0.7442643046379089, -0.40008631348609924)),100,Vector3.new(-319.3795471191406, 272.3931884765625, 388.7362060546875), Vector3.new(0.5347911715507507, -0.7442643046379089, -0.40008631348609924))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-315.74334716796875, 270.4518737792969, 307.21185302734375), Vector3.new(0.4924789369106293, -0.6783868670463562, -0.5452118515968323)),100,Vector3.new(-315.74334716796875, 270.4518737792969, 307.21185302734375), Vector3.new(0.4924789369106293, -0.6783868670463562, -0.5452118515968323))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-178.00997924804688, 272.4919128417969, 390.1238708496094), Vector3.new(0.6851771473884583, -0.678036093711853, -0.26608139276504517)),100,Vector3.new(-178.00997924804688, 272.4919128417969, 390.1238708496094), Vector3.new(0.6851771473884583, -0.678036093711853, -0.26608139276504517))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-159.9521026611328, 269.81768798828125, 312.1455993652344), Vector3.new(0.6065837144851685, -0.7200759649276733, -0.33696722984313965)),100,Vector3.new(-159.9521026611328, 269.81768798828125, 312.1455993652344), Vector3.new(0.6065837144851685, -0.7200759649276733, -0.33696722984313965))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(89.97474670410156, 299.3000183105469, -936.1035766601562), Vector3.new(0.2870140075683594, -0.6174480319023132, -0.7323803305625916)),100,Vector3.new(89.97474670410156, 299.3000183105469, -936.1035766601562), Vector3.new(0.2870140075683594, -0.6174480319023132, -0.7323803305625916))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1169.5670166015625, 219.90908813476562, -1588.0274658203125), Vector3.new(0.015137090347707272, -0.6970996260643005, -0.7168144583702087)),100,Vector3.new(-1169.5670166015625, 219.90908813476562, -1588.0274658203125), Vector3.new(0.015137090347707272, -0.6970996260643005, -0.7168144583702087))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1201.4923095703125, 254.11367797851562, -1660.2674560546875), Vector3.new(0.04675392061471939, -0.6955714225769043, -0.7169341444969177)),100,Vector3.new(-1201.4923095703125, 254.11367797851562, -1660.2674560546875), Vector3.new(0.04675392061471939, -0.6955714225769043, -0.7169341444969177))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1288.0887451171875, 245.90695190429688, -1653.00537109375), Vector3.new(0.025024037808179855, -0.7537118196487427, -0.6567284464836121)),100,Vector3.new(-1288.0887451171875, 245.90695190429688, -1653.00537109375))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1339.789306640625, 245.81817626953125, -1634.641845703125), Vector3.new(0.07458476722240448, -0.6587507128715515, -0.7486552596092224)),100,Vector3.new(-1339.789306640625, 245.81817626953125, -1634.641845703125), Vector3.new(0.07458476722240448, -0.6587507128715515, -0.7486552596092224))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1432.3958740234375, 256.3514709472656, -1652.33984375), Vector3.new(0.007446270436048508, -0.6148971319198608, -0.7885722517967224)),100,Vector3.new(-1432.3958740234375, 256.3514709472656, -1652.33984375), Vector3.new(0.007446270436048508, -0.6148971319198608, -0.7885722517967224))
wait(0.3)
game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(v,"QuakePower4", "StopCharging",workspace.IslandCaver.Stones.Stone,CFrame.new(Vector3.new(-1270.039794921875, 263.09088134765625, -1793.016357421875), Vector3.new(0.32165566086769104, -0.4306340515613556, -0.8432627320289612)),100,Vector3.new(-1270.039794921875, 263.09088134765625, -1793.016357421875), Vector3.new(0.32165566086769104, -0.4306340515613556, -0.8432627320289612))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandCaver"):WaitForChild("Stones"):WaitForChild("Stone"),
    [5] = CFrame.new(-1049.37659, 215, 1646.53479, 0.999993384, 0.00298895454, -0.00207511522, -0, 0.570294261, 0.821440458, 0.00363867474, -0.821435034, 0.570290446),
    [6] = 100,
    [7] = Vector3.new(-43.01959991455078, 216.19691467285156, -200.375732421875)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(-1048.52368, 215, 1683.08154, 0.969707072, 0.241547287, -0.0363770761, -0, 0.148920938, 0.988849103, 0.244271129, -0.958893955, 0.144409657),
    [6] = 100,
    [7] = Vector3.new(-47.42127990722656, 215.7339324951172, -202.49114990234375)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(-987.150879, 215, 1667.19971, 0.914944112, 0.390497267, -0.101927787, -0, 0.252558649, 0.96758157, 0.403580725, -0.885283053, 0.231077015),
    [6] = 100,
    [7] = Vector3.new(-42.87627029418945, 216.94845581054688, -200.90744018554688)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(4572.08203, 219.497177, 5281.18506, 0.653541863, -0.156973243, 0.740433991, -0, 0.978257895, 0.207392335, -0.756890297, -0.135539576, 0.639332533),
    [6] = 100,
    [7] = Vector3.new(-47.45362854003906, 217.59515380859375, -201.30079650878906)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(2150.41626, 216.977631, -620.214966, 0.542576551, -0.533092737, 0.649170995, -1.49011612e-08, 0.772816777, 0.634629369, -0.840006411, -0.34433502, 0.419312209),
    [6] = 100,
    [7] = Vector3.new(-45.78693389892578, 215.7545623779297, -203.71022033691406)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(2168.10864, 215.442368, -648.2948, 0.999150634, 0.0168674383, -0.0375972874, -9.31322686e-10, 0.912387192, 0.409328282, 0.0412076041, -0.408980608, 0.911612153),
    [6] = 100,
    [7] = Vector3.new(-46.27024459838867, 217.59515380859375, -199.48678588867188)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(2195.74121, 214.947037, -633.380371, 0.627761662, 0.333073497, -0.703546286, 1.49011612e-08, 0.903829932, 0.42789197, 0.778405607, -0.268614173, 0.567389786),
    [6] = 100,
    [7] = Vector3.new(-46.923622131347656, 217.59515380859375, -202.7979278564453)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(1135.47461, 221.200058, -3280.20483, 0.816403747, -0.3288019, 0.474736094, -0, 0.822080135, 0.569371998, -0.577481687, -0.464837432, 0.671149135),
    [6] = 100,
    [7] = Vector3.new(-80.33919525146484, 215.00575256347656, -884.0109252929688)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(1118.67578, 221.866333, -3374.4729, -0.639936566, -0.691518486, 0.33508715, 1.49011612e-08, 0.436068505, 0.89991349, -0.76842773, 0.575887561, -0.279056191),
    [6] = 100,
    [7] = Vector3.new(-76.82958221435547, 216.3629913330078, -881.9810791015625)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(1069.92468, 221.200027, -3394.1084, -0.861241043, 0.33216387, -0.384618104, -0, 0.756829202, 0.653612733, 0.508196771, 0.562918127, -0.651812315),
    [6] = 100,
    [7] = Vector3.new(-76.7877426147461, 216.2060546875, -882.0983276367188)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(995.937073, 221.200043, -3273.97607, -0.255309492, 0.30323121, -0.918078482, -7.45057971e-09, 0.949547052, 0.313624918, 0.9668594, 0.0800714269, -0.242428377),
    [6] = 100,
    [7] = Vector3.new(-81.3091049194336, 216.05020141601562, -884.2357788085938)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(-368.032806, 229.199478, -483.861359, -0.0814099088, 0.579163373, -0.811136484, -3.72528985e-09, 0.813837826, 0.581092179, 0.996680737, 0.0473066643, -0.0662544593),
    [6] = 100,
    [7] = Vector3.new(-80.90997314453125, 216.20582580566406, -884.9806518554688)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(-420.017883, 216.896423, -200.341003, 0.0463441163, 0.618907869, -0.784095347, -1.86264515e-09, 0.784938812, 0.619573534, 0.998925626, -0.0287135858, 0.0363772884),
    [6] = 100,
    [7] = Vector3.new(-81.10070037841797, 216.1497344970703, -884.7239379882812)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(61.3417625, 224.774521, -23.4785957, 0.00760989357, 0.389301956, -0.921078801, -2.32830644e-10, 0.921105444, 0.389313221, 0.999971032, -0.00296263187, 0.00700951461),
    [6] = 100,
    [7] = Vector3.new(-76.59005737304688, 216.6658477783203, -884.2120361328125)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(217.870819, 216.467972, 3.97104454, -0.0854031295, 0.680155993, -0.728075624, -0, 0.730745435, 0.682650089, 0.996346474, 0.0583004542, -0.0624079481),
    [6] = 100,
    [7] = Vector3.new(-81.43997955322266, 216.1997833251953, -882.7205200195312)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(78.618309, 225.43338, -250.790756, -0.931004524, -0.221155539, 0.290380716, -1.4901163e-08, 0.795546651, 0.605892539, -0.365007848, 0.564088702, -0.740657389),
    [6] = 100,
    [7] = Vector3.new(3.1437907218933105, 215.29119873046875, -200.572509765625)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)
local args = {
    [1] = v,
    [2] = "QuakePower4",
    [3] = "StopCharging",
    [4] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [5] = CFrame.new(-82.7837143, 213.28685, -292.159271, -0.953455389, -0.273064911, 0.127900094, -0, 0.424164504, 0.90558517, -0.301534206, 0.86343509, -0.404421896),
    [6] = 100,
    [7] = Vector3.new(-46.6608772277832, 215.0364990234375, -201.5364227294922)
}

game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
wait(0.3)

end)
end
end)

local ToggleA = Tab9.Main:AddToggle("MyToggle", {Title = "Refresh For Balance Lag (Every 30mins)", Default = false })

ToggleA:OnChanged(function(fc)
    getgenv().qw = fc
        while getgenv().qw do wait(1800)
            pcall(function()
game.Players.LocalPlayer.Character.Humanoid.Health = 0
game:GetService("Workspace").LocalPlayer.CharacterTrait.Health = 0
            end)
        end
    end)

local ToggleB = Tab9.Main:AddToggle("MyToggle", {Title = "Auto Respawn", Default = false })

ToggleB:OnChanged(function(spawn)
    _G.AutoSpawnn = spawn
end)

spawn(function()
    while wait() do
        if _G.AutoSpawnn then
            pcall(function()
                if game:GetService("Players").LocalPlayer.PlayerGui.Load.Frame.Visible == true then
                    repeat wait(3)
                        for i,v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Load.Frame.Load.MouseButton1Click)) do
                            v.Function()
                        end
                    until game:GetService("Players").LocalPlayer.PlayerGui.Load.Frame.Visible == false
                end
            end)
        end
    end
end)

Tab9.Main:AddParagraph({
    Title = "QUAKE FARM TP METHOD",
    Content = "QUAKE FARM(TP METHOD)"
})

local Togglefkw = Tab9.Main:AddToggle("MyToggle", {Title = "TQuake Farm (Use Skill To Active)", Default = false })

Togglefkw:OnChanged(function(tpfarmquake)
    getgenv().quakeeeeeee = tpfarmquake
while getgenv().quakeeeeeee do wait()
pcall(function()
        if getgenv().quakeeeeeee then
            local pla = game.Players.LocalPlayer;
            local Mouse = pla:GetMouse();
            function round(num, numDecimalPlaces)
                local mult = 10 ^ (numDecimalPlaces or 0)
                return math.floor(num * mult + 0.6) / mult
            end

            local humanoid = game.Players.LocalPlayer.Character.HumanoidRootPart

            Xx = humanoid.Position.x-- round(humanoid.Position.x, 0)
            Yy = humanoid.Position.y--round(humanoid.Position.y, 0)
            Zz = humanoid.Position.z--round(humanoid.Position.z, 0)
local args = {
                [1] = tonumber(serializeTable(remotes)),
                [2] = "QuakePower3",
                [3] = "StartCharging",
                [5] = "Right"
            }

            game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
   wait()
            local args = {
                [1] = tonumber(serializeTable(remotes)),
                [2] = "QuakePower3",
                [3] = "StopCharging",
                [4] = Mouse.Target,
                [5] = Mouse.Hit,
                [6] = 100,
                [7] = Vector3.new(Xx, Yy, Zz)
            }

            game:GetService("Players").LocalPlayer.Character.Powers.Quake.RemoteEvent:FireServer(unpack(args))
   wait(0.5)
   end
   end)
   end
end)

Tab9.Main:AddParagraph({
    Title = "Light Farm",
    Content = "Farm with Light Fruit"
})

local Togglemwk = Tab9.Main:AddToggle("MyToggle", {Title = "Light Farm", Default = false })

Togglemwk:OnChanged(function(tpmodelight)
    getgenv().lightttt = tpmodelight
        while getgenv().lightttt do wait()
    pcall(function()
local x = getsenv(game:GetService("Players").LocalPlayer.Character.Powers.Light)
local v = x.VTCrv
game:GetService("Players").LocalPlayer.Character.Powers.Light.RemoteEvent:FireServer(v,"LightPower2", "StartCharging",CFrame.new(Vector3.new(-1037.58544921875, 215.7229461669922, -5000.449951171875), Vector3.new(-0.7139230966567993, -0.5779988169670105, 0.39526084065437317)),workspace.IslandCaver.Stones.Stone, 100)
wait()
local args = {
    [1] = v,
    [2] = "LightPower2",
    [3] = "StopCharging",
    [4] = CFrame.new(-1084.59033, -9763.44336, 501.375885, -0, 0.995015204, 0.0997241139, 0.0880244896, -0.099337019, 0.991152883, 0.996118307, 0.00877816416, -0.08758571),
    [5] = workspace:WaitForChild("IslandWindmill"):WaitForChild("Beach"):WaitForChild("Beach"),
    [6] = 100
}

game:GetService("Players").LocalPlayer.Character.Powers.Light.RemoteEvent:FireServer(unpack(args))
wait(0.1)
end)
end
end)

