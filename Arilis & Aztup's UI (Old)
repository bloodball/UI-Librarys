--Made by : https://v3rmillion.net/member.php?action=profile&uid=536485 (I don't know Aztups v3rmillion.)

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
