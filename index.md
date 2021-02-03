## Welcome to Graveyard's UI Archive. 

Modern UI.
```lua
local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/modern"))()
local ExampleTab = Lib:Tab("ExampleTab")
ExampleTab:Button("Hello World!", function()
print("Hello World!")
end)
ExampleTab:Label("ExampleLabel", "Exaple Label")
ExampleTab:TextBox("Example Text Box", function(text)
print(text)
end)
ExampleTab:Toggle("Example Toggle", function(state)
if state then
PrintToggle = true
while PrintToggle do
print("Hello Toggle!")
wait()
end
else
PrintToggle = false
end
end)
ExampleTab:DropDown("Example DropDown", {"Sentinel", "Shitnapse X", "ProtoCrasher"}, function(text)
if text == "Sentinel" then
print("Best Lego Hak")
warn("but small memory")
elseif text == "Shitnapse X" then
print("plz update faster", "discord server is full of nub")
elseif text == "ProtoCrasher" then
print("i liek cresh")
end
end)
```
----------------------------------------------------------------------------------------------------
Coasting UI.
```lua
local CoastingLibrary = loadstring(game:HttpGet("https://pastebin.com/raw/3gQQtaKX"))()

local AimbotTab = CoastingLibrary:CreateTab("Aimbot")
local MainSection = AimbotTab:CreateSection("Main")
local ConfigSection = AimbotTab:CreateSection("Config")

MainSection:CreateButton("Click Me!", function()
   print("Boo!")    
end)

MainSection:CreateLabel("Namey", "Hello!")

MainSection:CreateToggle("Aimbot", function(boolean)
   print("Aimbot:", boolean)
end)

MainSection:CreateSlider("Field Of View", 0, 150, 50, false, function(value)
   print("Field of View: " .. value)
end)

ConfigSection:CreateColorPicker("Field of View Color", Color3.fromRGB(255, 255, 255), function(color)
   print("Field Of View Color:", color)
end)

ConfigSection:CreateDropdown("Type", {"Mouse", "Character"}, 1, function(option)
   print("Type: " .. option)
end)

ConfigSection:CreateKeybind("Aimbot Bind", Enum.KeyCode.Unknown, false, true, function(boolean)
   print("Aimbot Active:", boolean)
end)
```
----------------------------------------------------------------------------------------------------
0x37's UI Library.
```lua
local library = loadstring(game.HttpGet(game, "https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/0x"))()

local w1 = library:Window("a") -- Text

w1:Button(
    "Print Hi",
    function()
        print("Hi")
    end
) -- Text, Callback

w1:Slider(
    "WalkSpeed",
    "WS",
    16,
    300,
    function(value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
    end
) -- Text, Flag, Minimum, Maximum, Callback, Default (Optional), Flag Location (Optional)

w1:Slider(
    "JumpPower",
    "JP",
    50,
    300,
    function(value)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = value
    end,
    100
) -- Text, Flag, Minimum, Maximum, Callback, Default (Optional), Flag Location (Optional)

w1:Toggle(
    "Freeze",
    "frz",
    false,
    function(toggled)
        game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = toggled
    end
) -- Text, Flag, Enabled, Callback, Flag Location (Optional)

w1:Button(
    "Destroy GUI",
    function()
        for i, v in pairs(game.CoreGui:GetChildren()) do
            if v:FindFirstChild("Top") then
                v:Destroy()
            end
        end
    end
) -- Text, Callback

w1:Label("0 x 3 7") -- Text
```
----------------------------------------------------------------------------------------------------
Arilis & Aztup's UI (Old).
```lua
local library = loadstring(game:HttpGet('https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/Create%20Arilis%20%26%20Aztup's%20UI%20(Old)', true))()
local main = library:CreateWindow('Main')
local resetChar = main:Button('Reset Character', function()
    game:GetService('Players').LocalPlayer.Character:BreakJoints()
end)

local walkspeedBox = main:Box('Walkspeed', '16', function(value)
    game:GetService('Players').LocalPlayer.Character.Humanoid.WalkSpeed = value
end)

local toggleJumpHeight = main:Toggle('JumpPower Toggle', function(state)
    if state then
        game:GetService('Players').LocalPlayer.Character.Humanoid.JumpPower = 200
    else
        game:GetService('Players').LocalPlayer.Character.Humanoid.JumpPower = 50
    end
end)

local autofarmSection = main:Section('Auto-Farm Section')

local colorPicker = main:ColorPicker("ESP Color", Color3.fromRGB(255, 0, 0), function(color)
    print(color)
end)

local hipHeightSlider = main:Slider('Hip Height', {min = 0, max = 20, default = 0}, function(value)
    game:GetService('Players').LocalPlayer.Character.Humanoid.HipHeight = value
end)

local sitBind = main:Bind('Sit Keybind', Enum.KeyCode.V, function(new)
    if sitBind then
        game:GetService('Players').LocalPlayer.Character.Humanoid.Sit = true
    else
        game:GetService('Players').LocalPlayer.Character.Humanoid.Sit = false
    end
end)
```
----------------------------------------------------------------------------------------------------
Bacon Lib.
```lua
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/bacon"))()
local version, changelog = lib:GetInfo()
local window = lib:CreateWindow("BaconLib v"..version)
local label = lib:CreateLabel(window, "Main")
local textBox = lib:CreateTextBox(window, Enum.Font.Legacy, "Text", "Hello, World!")

local button = lib:CreateButton(window, "Print Text", function()
    print(textBox.Text)
end)

local toggled = false
local toggle = lib:CreateToggle(window, "Spam Warn 'Hello'", false, function(toggleState)
    toggled = not toggled
    while toggled and game:GetService('RunService').Heartbeat:Wait() do
        warn("Hello")
    end
end)

local drop = lib:CreateDropdown(window, "Dropdown")
lib:NewDropdownButton(window, drop, "Print 'LOL'", function()
   print("LOL")
end)

lib:NewDropdownButton(window, drop, "Print 'YES'", function()
   print("YES")
end)

lib:NewDropdownButton(window, drop, "Warn 'XD'", function()
   warn("XD")
end)

local slider = lib:CreateSlider(window, "Print Value", 0, 100, 50, function(value)
    print(value)
end)

local keybind = lib:CreateKeyBind(window, "Print Key", "z", function(key)
    print(key)
end)
```
----------------------------------------------------------------------------------------------------
Coasting Old.
```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/coast%20old"))()
local test = Library:CreateTab("Title", "Description")

test:CreateButton("Button", function()
end)

test:CreateSection("Section")

test:CreateCheckbox("Checkbox", function()
end)

test:CreateSlider("Slider", 50,0,0,0 , function()
    end)


```
----------------------------------------------------------------------------------------------------
Coollib V2.
```lua
--[[
Theme = {
["MainColor"] = Color3.fromRGB(20, 20, 20);
["BackColor"] = Color3.fromRGB(10, 10, 10);
["AccentRGB"] = Color3.fromRGB(64, 51, 145);
["ToggleRGB"] = Color3.fromRGB(64, 51, 145);
}
]]--
local library = loadstring(game:HttpGet("https://wally-hub.eats-shit.xyz/images/ql0tevzglj94.txt"))()
local tab1 = library.newTab("Local")
local tab3 = library.newTab("ESP")
local tab2 = library.newTab("Settings")
kys = function()
game:GetService("Players").LocalPlayer.Character:BreakJoints()
end
tab1.addbtn("die", kys)
tab1.addtoggle("WS Enabled", "wsenb", function(enb) end)
tab1.addbox("WS Value", "wsvalue", 16, function(value) end)
game:GetService("RunService").RenderStepped:Connect(function()
if library.flags["wsenb"] == false then
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
else
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = library.flags["wsvalue"]
end
end)
tab2.addbtn("Destroy GUI", function() for i,v in pairs(game.CoreGui:GetChildren()) do if v.Name == "UiLib" then v:Destroy() end end end)
tab2.addbox("Title", "titleflag", "Title Here", function(lol) end)
tab2.addbox("Duration", "durflag", 1, function(ggg) end)
tab2.addbox("Description", "descflag", "Description", function(ll) end)
tab2.addbtn("Send Notification", function()
game:GetService("StarterGui"):SetCore("SendNotification", {
Title = library.flags["titleflag"],
Duration = tostring(library.flags["durflag"]),
Text = library.flags["descflag"]
})
end)
```
----------------------------------------------------------------------------------------------------
Dirt
```lua
local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/dirt",true))()
local Table = {}
local window = Lib:CreateWindow("Nice")
window:Section("Section")
window:Button("Button",function()
   print("Nice")
end)
window:Toggle("Toggle",{location = Table, flag = "Toggle"},function()
   print(Table["Toggle"])
end)
window:Slider("Slider",{location = Table, min = 1, max = 64, default = 32, precise = true --[[ 0.00 instead of 0 ]], flag = "Slider"},function()
   print(Table["Slider"])
end)
window:Dropdown("Dropdown",{location = Table,flag = "Dropdown",search = true --[[AddsSearchBar]], list = {"1","2","3","4","5","6","7","8","9","0"} --[[Wont work when PlayerList = true]], PlayerList = true --[[ Turns the list into the players in the server ]]},function()
   print(Table["Dropdown"])
end)
window:Bind("KeyBind",{location = Table, flag = "KeyBind", default = Enum.KeyCode.B},function() -- Automatically stops when the gui is removed
   print(Table["KeyBind"])
end)
window:Box("Box",{location = Table,flag = "Box", type = "number" --[[ Only Numbers automatically on false ]], hold = "Numbers" --[[ PlaceHolderText ]]},function()
   print(Table["Box"])
end)
window:Search(Color3.fromRGB(255,0,255) --[[nil = Yellow]]) -- Ez searcher for if you have a lot of things
window:String({string = "String"})
```
## This is unfinished! I will put the remainder of them on here in due time.
