_G.Visible = true;

game:GetService("UserInputService").InputBegan:Connect(function(Key, _)
    if not _ and Key.KeyCode == Enum.KeyCode.RightControl then
        _G.Visible = not _G.Visible;
    end
end)

for i,v in pairs(game.CoreGui:GetChildren()) do
	if v.Name == "Celestron" then
		v:Destroy()
	end
end

if _G.Visible = true then
    Top.Visible = false
elseif _G.Visible = false then
    Top.Visible = false
end

local Celestron = Instance.new("ScreenGui")
Celestron.Name = "Celestron"
Celestron.Parent = game.CoreGui
Celestron.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local function getNextWindowPos()
	local biggest = 0;
	local ok = nil;
	for i, v in pairs(Celestron:GetChildren()) do
		if v.Position.X.Offset > biggest then
			biggest = v.Position.X.Offset
			ok = v;
		end
	end
	if biggest == 0 then
		biggest = biggest + 15;
	else
		biggest = biggest + ok.Size.X.Offset + 10;
	end
	
	return biggest;
end

local Library = {}

function Library:Window(title)
	local Top = Instance.new("Frame")
	local UICorner = Instance.new("UICorner")
	local Container = Instance.new("Frame")
	local UIListLayout_2 = Instance.new("UIListLayout")
	local Line = Instance.new("Frame")
	local Title = Instance.new("TextLabel")
	local Minimize = Instance.new("ImageButton")

	Top.Name = "Top"
	Top.Parent = Celestron
	Top.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	Top.BorderSizePixel = 0
	Top.Position = UDim2.new(0, getNextWindowPos(), 0.01, 0)
	Top.Size = UDim2.new(0, 204, 0, 28)
	Top.Active = true
    Top.Draggable = true

	UICorner.CornerRadius = UDim.new(0, 4)
	UICorner.Parent = Top

	Container.Name = "Container"
	Container.Parent = Top
	Container.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Container.BackgroundTransparency = 1.000
	Container.ClipsDescendants = true
	Container.Position = UDim2.new(0, 0, 1, 0)
	Container.Size = UDim2.new(0, 204, 0, 762)

	UIListLayout_2.Parent = Container
	UIListLayout_2.HorizontalAlignment = Enum.HorizontalAlignment.Center
	UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder

	Line.Name = "Line"
	Line.Parent = Top
	Line.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	Line.BorderSizePixel = 0
	Line.Position = UDim2.new(0, 0, 0.892857134, 0)
	Line.Size = UDim2.new(0, 204, 0, 3)

	Title.Name = "Title"
	Title.Parent = Top
	Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Title.BackgroundTransparency = 1.000
	Title.Position = UDim2.new(0.0245098043, 0, 0.142857149, 0)
	Title.Size = UDim2.new(0, 174, 0, 20)
	Title.Font = Enum.Font.GothamSemibold
	Title.Text = title
	Title.TextColor3 = Color3.fromRGB(255, 255, 255)
	Title.TextScaled = true
	Title.TextSize = 14.000
	Title.TextWrapped = true
	Title.TextXAlignment = Enum.TextXAlignment.Left

	Minimize.Name = "Minimize"
	Minimize.Parent = Top
	Minimize.BackgroundTransparency = 1.000
	Minimize.Position = UDim2.new(0.877451003, 0, 0, 0)
	Minimize.Rotation = 90.000
	Minimize.Size = UDim2.new(0, 25, 0, 25)
	Minimize.ZIndex = 2
	Minimize.Image = "rbxassetid://3926307971"
	Minimize.ImageColor3 = Color3.fromRGB(0, 255, 102)
	Minimize.ImageRectOffset = Vector2.new(764, 244)
	Minimize.ImageRectSize = Vector2.new(36, 36)

	local function UZVNGAL_fake_script() -- Minimize.Script 
		local script = Instance.new('Script', Minimize)

		script.Parent.MouseButton1Click:Connect(function()
			if script.Parent.Parent.Container.Size == UDim2.new(0, 204,0, 762) then 
				game:GetService("TweenService"):Create(script.Parent, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = 180}):Play();
				game:GetService("TweenService"):Create(script.Parent, TweenInfo.new(0.25), {ImageColor3 = Color3.fromRGB(255, 0, 68)}):Play()
				script.Parent.Parent.Container:TweenSize(UDim2.new(0, 204,0, 0), "InOut", "Sine", 0.25, true)
				wait(0.25)
				script.Parent.Parent.Line.Visible = false
			else
				game:GetService("TweenService"):Create(script.Parent, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = 90}):Play();
				game:GetService("TweenService"):Create(script.Parent, TweenInfo.new(0.25), {ImageColor3 = Color3.fromRGB(0, 255, 102)}):Play()
				script.Parent.Parent.Container:TweenSize(UDim2.new(0, 204,0, 762), "InOut", "Sine", 0.2, true)
				script.Parent.Parent.Line.Visible = true
			end
		end)
	end
	coroutine.wrap(UZVNGAL_fake_script)()
	
	local Lib = {}
	
	function Lib:Button(name, callback)
		local ButtonContainer = Instance.new("Frame")
		local Button = Instance.new("TextButton")
		local ButtonAni = Instance.new("Frame")
		local UICorner_2 = Instance.new("UICorner")
		local UIListLayout = Instance.new("UIListLayout")
		local ButtonName = Instance.new("TextLabel")
		
		ButtonContainer.Name = "ButtonContainer"
		ButtonContainer.Parent = Container
		ButtonContainer.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
		ButtonContainer.BorderSizePixel = 0
		ButtonContainer.Size = UDim2.new(0, 204, 0, 28)
		
		Button.Name = "Button"
		Button.Parent = ButtonContainer
		Button.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Button.BackgroundTransparency = 1.000
		Button.Size = UDim2.new(0, 204, 0, 28)
		Button.Font = Enum.Font.SourceSans
		Button.Text = ""
		Button.TextColor3 = Color3.fromRGB(0, 0, 0)
		Button.TextSize = 14.000
		Button.MouseButton1Click:Connect(function()
			callback()
		end)
		
		ButtonAni.Name = "ButtonAni"
		ButtonAni.Parent = Button
		ButtonAni.BackgroundColor3 = Color3.fromRGB(0, 255, 102)
		ButtonAni.Position = UDim2.new(0.0245098043, 0, 0.0714285746, 0)
		
		UICorner_2.CornerRadius = UDim.new(0, 4)
		UICorner_2.Parent = ButtonAni
		
		UIListLayout.Parent = Button
		UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout.VerticalAlignment = Enum.VerticalAlignment.Center
		
		ButtonName.Name = "ButtonName"
		ButtonName.Parent = ButtonContainer
		ButtonName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ButtonName.BackgroundTransparency = 1.000
		ButtonName.Position = UDim2.new(0.0245098043, 0, 0.142857149, 0)
		ButtonName.Size = UDim2.new(0, 194, 0, 20)
		ButtonName.ZIndex = 3
		ButtonName.Font = Enum.Font.GothamSemibold
		ButtonName.Text = name
		ButtonName.TextColor3 = Color3.fromRGB(255, 255, 255)
		ButtonName.TextScaled = true
		ButtonName.TextSize = 14.000
		ButtonName.TextWrapped = true
		
		local function ZNVYM_fake_script() -- Button.Script 
			local script = Instance.new('Script', Button)
			
			script.Parent.MouseButton1Click:Connect(function()
				script.Parent.ButtonAni:TweenSize(UDim2.new(0, 194,0, 24), 'InOut', "Sine", 0.3, true)
				wait(0.45)
				script.Parent.ButtonAni:TweenSize(UDim2.new(0, 0, 0, 0), "InOut", "Sine", 0.3, true)
			end)
		end
		coroutine.wrap(ZNVYM_fake_script)()
	end
	
	function Lib:Toggle(name, callback)
		local ToggleContainer = Instance.new("Frame")
		local ToggleName = Instance.new("TextLabel")
		local Toggle = Instance.new("TextButton")
		local UICorner_3 = Instance.new("UICorner")
		local Off = Instance.new("ImageLabel")
		local On = Instance.new("ImageLabel")
		
		ToggleContainer.Name = "ToggleContainer"
		ToggleContainer.Parent = Container
		ToggleContainer.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
		ToggleContainer.BorderSizePixel = 0
		ToggleContainer.Size = UDim2.new(0, 204, 0, 30)
		
		ToggleName.Name = "ToggleName"
		ToggleName.Parent = ToggleContainer
		ToggleName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ToggleName.BackgroundTransparency = 1.000
		ToggleName.Position = UDim2.new(0.0245098043, 0, 0.142857105, 0)
		ToggleName.Size = UDim2.new(0, 169, 0, 20)
		ToggleName.Font = Enum.Font.GothamSemibold
		ToggleName.Text = name
		ToggleName.TextColor3 = Color3.fromRGB(255, 255, 255)
		ToggleName.TextScaled = true
		ToggleName.TextSize = 14.000
		ToggleName.TextWrapped = true
		ToggleName.TextXAlignment = Enum.TextXAlignment.Left
		
		Toggle.Name = "Toggle"
		Toggle.Parent = ToggleContainer
		Toggle.BackgroundColor3 = Color3.fromRGB(39, 39, 39)
		Toggle.BorderColor3 = Color3.fromRGB(27, 42, 53)
		Toggle.Position = UDim2.new(0.852941215, 0, 0.0666666627, 0)
		Toggle.Size = UDim2.new(0, 25, 0, 23)
		Toggle.AutoButtonColor = false
		Toggle.Font = Enum.Font.SourceSans
		Toggle.Text = ""
		Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)
		Toggle.TextSize = 14.000
		local Toggled = false
		Toggle.MouseButton1Click:Connect(function()
			if Toggled == false then
				Toggled = true
			else
				Toggled = false
			end
			callback(Toggled)
		end)
		
		UICorner_3.CornerRadius = UDim.new(0, 3)
		UICorner_3.Parent = Toggle
		
		Off.Name = "Off"
		Off.Parent = Toggle
		Off.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Off.BackgroundTransparency = 1.000
		Off.Size = UDim2.new(0, 25, 0, 25)
		Off.Image = "rbxassetid://3926305904"
		Off.ImageColor3 = Color3.fromRGB(255, 0, 68)
		Off.ImageRectOffset = Vector2.new(924, 724)
		Off.ImageRectSize = Vector2.new(36, 36)
		
		On.Name = "On"
		On.Parent = Toggle
		On.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		On.BackgroundTransparency = 1.000
		On.Size = UDim2.new(0, 25, 0, 25)
		On.Visible = false
		On.Image = "rbxassetid://3926305904"
		On.ImageColor3 = Color3.fromRGB(0, 255, 102)
		On.ImageRectOffset = Vector2.new(312, 4)
		On.ImageRectSize = Vector2.new(24, 24)
		
		local function XLZZDX_fake_script() -- Toggle.Script 
			local script = Instance.new('Script', Toggle)
			
			script.Parent.MouseButton1Click:Connect(function()
				if script.Parent.Off.Rotation == 0 then
					script.Parent.On.Rotation = 0
					game:GetService("TweenService"):Create(script.Parent.Off, TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = 360}):Play();
					wait(0.3)
					script.Parent.Off.Visible = false
					script.Parent.On.Visible = true
				else
					script.Parent.Off.Rotation = 0
					game:GetService("TweenService"):Create(script.Parent.On, TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = -360}):Play();
					wait(0.3)
					script.Parent.On.Visible = false
					script.Parent.Off.Visible = true
				end
			end)
		end
		coroutine.wrap(XLZZDX_fake_script)()
	end
	
	return Lib
	
end

return Library
