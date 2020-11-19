--Lib made by: LycorisUser.

local library = {}
local oldcam = workspace.CurrentCamera.CameraType
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game:GetService("CoreGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Name = "LyHub"

local Tabs = Instance.new("Folder")
Tabs.Parent = ScreenGui
Tabs.Name = "Tabs"

local tb = Instance.new("TextButton")
tb.Parent = ScreenGui
tb.Modal = true
tb.Name = " "
tb.Visible = true
tb.Size = UDim2.new(0,0,0,0)
tb.BorderSizePixel = 0

local plrs = game:GetService("Players")
local mouse = plrs.LocalPlayer:GetMouse()
local uis = game:GetService("UserInputService")
local ts = game:GetService("TweenService")
local rs = game:GetService("RunService")

getgenv().a = true
getgenv().fov = 70
uis.MouseIconEnabled = true

getgenv().oldCam = workspace.CurrentCamera.CameraType
function library:Destroy()
	ScreenGui:Destroy()
	game:GetService("Lighting"):FindFirstChild("LBlur"):Destroy()
	game:GetService("Lighting"):FindFirstChild("LColor"):Destroy()
	game.Workspace.CurrentCamera.FieldOfView = 70
	game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Anchored = false
	game.Workspace.CurrentCamera.CameraType = oldcam
end
function library:New()
	local Tabs = Instance.new("Folder")
	Tabs.Name = "Tabs"
	Tabs.Parent = ScreenGui

	local xa = Instance.new("BlurEffect")
	xa.Size = 24
	xa.Parent = game:GetService("Lighting")
	xa.Name = "LBlur"

	local xe = Instance.new("ColorCorrectionEffect")
	xe.Name = "LColor"
	xe.Saturation = -1
	xe.Parent = game:GetService("Lighting")

	local lastPos = UDim2.new(0, 13, 0, 16)
	local posCount = 0
	getgenv().keybind = "P"

	local t2 = ts:Create(workspace.CurrentCamera, TweenInfo.new(.2), {FieldOfView = 40})
	t2:Play()
	workspace.CurrentCamera.CameraType = Enum.CameraType.Scriptable
	local sound = Instance.new("Sound")
	sound.Parent = workspace
	sound.SoundId = 'rbxassetid://138097048'
	if not sound.IsLoaded then
		sound.Loaded:wait()
	end
	sound:Play()
	local open = true
	local creator = {}
	uis.InputBegan:Connect(function(a, f)
		if not f then
			if a.KeyCode == Enum.KeyCode[getgenv().keybind] and getgenv().a then
				open = not open
				if open then
					for i, v in pairs(Tabs:GetChildren()) do
						v.Visible = true
					end
					xa.Enabled = true
					tb.Visible = true
					local t = ts:Create(xe, TweenInfo.new(.2), {Saturation = -1})
					t:Play()
					sound:Play()
					local t2 = ts:Create(workspace.CurrentCamera, TweenInfo.new(.5, Enum.EasingStyle.Quint, Enum.EasingDirection.Out), {FieldOfView = 40})
					t2:Play()
					uis.MouseIconEnabled = true
					workspace.CurrentCamera.CameraType = Enum.CameraType.Scriptable
					plrs.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Anchored = true
				else
					for i, v in pairs(Tabs:GetChildren()) do
						v.Visible = false
					end
					tb.Visible = false
					xa.Enabled = false
					local t = ts:Create(xe, TweenInfo.new(.2), {Saturation = 0})
					t:Play()
					sound:Play()
					local t2 = ts:Create(workspace.CurrentCamera, TweenInfo.new(.15, Enum.EasingStyle.Quint, Enum.EasingDirection.In), {FieldOfView = getgenv().fov})
					t2:Play()
					uis.MouseIconEnabled = true
					workspace.CurrentCamera.CameraType = getgenv().oldCam
					plrs.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Anchored = false
				end
			end
		end
	end)

	function creator:Tab(name, tab)
		local ysize = 0
		name = name or "Tab"
		local toggle = false
		tab = string.upper(tab) or "TAB"
		local TAB = Instance.new("Frame")
		local Title = Instance.new("TextLabel")
		local Holder = Instance.new("Frame")
		local Frame = Instance.new("Frame")
		local UIListLayout = Instance.new("UIListLayout")

		TAB.Name = tab
		TAB.Parent = Tabs
		TAB.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
		TAB.BorderColor3 = Color3.fromRGB(0, 132, 255)
		TAB.Position = lastPos
		TAB.Size = UDim2.new(0, 198, 0, 33)

		Title.Name = "Title"
		Title.Parent = TAB
		Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title.BackgroundTransparency = 1.000
		Title.BorderSizePixel = 0
		Title.Position = UDim2.new(0, 6, 0, 0)
		Title.Size = UDim2.new(0, 183, 0, 33)
		Title.Font = Enum.Font.GothamSemibold
		Title.Text = name
		Title.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title.TextSize = 17.000
		Title.TextWrapped = true
		Title.TextXAlignment = Enum.TextXAlignment.Left

		Holder.Name = "Holder"
		Holder.Parent = TAB
		Holder.BackgroundColor3 = Color3.fromRGB(38, 38, 38)
		Holder.BorderSizePixel = 0
		Holder.ClipsDescendants = true
		Holder.Position = UDim2.new(0, 0, 0, 33)
		Holder.Size = UDim2.new(0, 198, 0, 0)

		Frame.Parent = Holder
		Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Frame.BackgroundTransparency = 1.000
		Frame.BorderSizePixel = 0
		Frame.Position = UDim2.new(0, 3, 0, 3)
		Frame.Size = UDim2.new(0, 190, 0, 0)

		UIListLayout.Parent = Frame
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout.Padding = UDim.new(0, 5)

		TAB.InputBegan:Connect(function(a, b)
			if not b then
				if a.UserInputType == Enum.UserInputType.MouseButton2 then
					toggle = not toggle
					if toggle then
						Holder:TweenSize(UDim2.new(0, 198, 0, ysize), "Out", "Quint", 0.2, true)
					else
						Holder:TweenSize(UDim2.new(0, 198, 0, 0), "Out", "Quint", 0.2, true)
					end
				end
			end
		end)

		function updateSize(x)
			ysize = ysize + x
			print(Frame.Size)
		end
		local gui = TAB
		local dragging
		local dragInput
		local dragStart
		local startPos

		local function update(input)
			local delta = input.Position - dragStart
			gui:TweenPosition(UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y), "Out", "Quint", 0.2, true)
		end

		gui.InputBegan:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				dragging = true
				dragStart = input.Position
				startPos = gui.Position

				input.Changed:Connect(function()
					if input.UserInputState == Enum.UserInputState.End then
						dragging = false
					end
				end)
			end
		end)

		gui.InputChanged:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
				dragInput = input
			end
		end)

		uis.InputChanged:Connect(function(input)
			if input == dragInput and dragging then
				update(input)
			end
		end)
		local curr = TAB.AbsolutePosition.Y + 60
		if posCount == 4 then
			lastPos = UDim2.new(0, 13, 0, curr)
			posCount = 0
		else
			lastPos = lastPos + UDim2.new(0, 210, 0, 0)
			posCount = posCount + 1
		end
	end

	function creator:Toggle(name, tab, callback)
		name = name or "Toggle"
		tab = string.upper(tab) or "TAB"
		callback = callback or function() end

		updateSize(35)
		local Toggle = Instance.new("Frame")
		local Name = Instance.new("TextLabel")
		local Back = Instance.new("Frame")
		local TheToggle = Instance.new("Frame")
		local t = false
		Toggle.Name = "Toggle"
		Toggle.Parent = Tabs[tab]["Holder"]["Frame"]
		Toggle.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
		Toggle.BorderSizePixel = 0
		Toggle.Size = UDim2.new(0, 192, 0, 28)

		Name.Name = "Name"
		Name.Parent = Toggle
		Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Name.BackgroundTransparency = 1.000
		Name.BorderSizePixel = 0
		Name.Position = UDim2.new(0.0157894734, 0, 0, 0)
		Name.Size = UDim2.new(0, 154, 0, 28)
		Name.Font = Enum.Font.Gotham
		Name.Text = name
		Name.TextColor3 = Color3.fromRGB(186, 186, 186)
		Name.TextSize = 14.000
		Name.TextWrapped = true
		Name.TextXAlignment = Enum.TextXAlignment.Left

		Back.Name = "Back"
		Back.Parent = Toggle
		Back.BackgroundColor3 = Color3.fromRGB(56, 56, 56)
		Back.BorderSizePixel = 0
		Back.Position = UDim2.new(0, 165, 0, 3)
		Back.Size = UDim2.new(0, 22, 0, 22)

		TheToggle.Name = "TheToggle"
		TheToggle.Parent = Back
		TheToggle.AnchorPoint = Vector2.new(0.5, 0.5)
		TheToggle.BackgroundColor3 = Color3.fromRGB(0, 145, 255)
		TheToggle.BorderSizePixel = 0
		TheToggle.Position = UDim2.new(0.5, 0, 0.5, 0)

		Back.InputBegan:Connect(function(a, b)
			if not b then
				if a.UserInputType == Enum.UserInputType.MouseButton1 then
					t = not t
					if t then
						TheToggle:TweenSize(UDim2.new(0,22,0,22), "Out", "Quint", 0.1, true)
					else
						TheToggle:TweenSize(UDim2.new(0,0,0,0), "Out", "Quint", 0.1, true)
					end
					pcall(callback)
				end
			end
		end)
	end

	function creator:Label(text, tab, callback)
		text = text or "yo"
		tab = string.upper(tab) or "TAB"
		callback = callback or function() end

		local Label = Instance.new("Frame")
		local Text = Instance.new("TextLabel")

		Label.Name = "Label"
		Label.Parent = Tabs[tab]["Holder"]["Frame"]
		Label.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
		Label.BorderSizePixel = 0
		Label.Size = UDim2.new(0, 192, 0, 28)

		Text.Name = "Text"
		Text.Parent = Label
		Text.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Text.BackgroundTransparency = 1.000
		Text.BorderSizePixel = 0
		Text.Position = UDim2.new(0, 2, 0, 0)
		Text.Size = UDim2.new(0, 184, 0, 28)
		Text.Font = Enum.Font.Gotham
		Text.Text = text
		Text.TextColor3 = Color3.fromRGB(186, 186, 186)
		Text.TextSize = 14.000
		Text.TextWrapped = true
		Text.RichText = true
		Text.TextTruncate = Enum.TextTruncate.AtEnd

		local function updateY()
			Label.Size = UDim2.new(0, 190, 0, Text.TextBounds.Y)
			Text.Size = UDim2.new(0, 184, 0, Text.TextBounds.Y)
		end
		updateY()
		updateSize(tonumber(Text.AbsoluteSize.Y + 7))
		callback(Text)
	end

	function creator:Slider(name, tab, minvalue, maxvalue, defaultvalue, callback)
		name = name or "Slider"
		tab = string.upper(tab) or "TAB"
		minvalue = minvalue or 0
		maxvalue = maxvalue or 100
		defaultvalue = defaultvalue or 100
		callback = callback or function() end
		local value = defaultvalue or 0
		pcall(function()
			callback(defaultvalue)
		end)

		local Slider = Instance.new("Frame")
		local Name = Instance.new("TextLabel")
		local Back = Instance.new("Frame")
		local TheSlider = Instance.new("Frame")
		local Value = Instance.new("TextLabel")

		Slider.Name = "Slider"
		Slider.Parent = Tabs[tab]["Holder"]["Frame"]
		Slider.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
		Slider.BorderSizePixel = 0
		Slider.Position = UDim2.new(0, 0, 0.540983617, 0)
		Slider.Size = UDim2.new(0, 190, 0, 44)

		Name.Name = "Name"
		Name.Parent = Slider
		Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Name.BackgroundTransparency = 1.000
		Name.BorderSizePixel = 0
		Name.Position = UDim2.new(0.0157894734, 0, 0, 0)
		Name.Size = UDim2.new(0, 154, 0, 28)
		Name.Font = Enum.Font.Gotham
		Name.Text = name
		Name.TextColor3 = Color3.fromRGB(186, 186, 186)
		Name.TextSize = 14.000
		Name.TextWrapped = true
		Name.TextXAlignment = Enum.TextXAlignment.Left

		Back.Name = "Back"
		Back.Parent = Slider
		Back.BackgroundColor3 = Color3.fromRGB(56, 56, 56)
		Back.BorderSizePixel = 0
		Back.Position = UDim2.new(0, 3, 0, 28)
		Back.Size = UDim2.new(0, 184, 0, 11)

		TheSlider.Name = "TheSlider"
		TheSlider.Parent = Back
		TheSlider.BackgroundColor3 = Color3.fromRGB(0, 145, 255)
		TheSlider.BorderSizePixel = 0
		TheSlider.Size = UDim2.new(0, 184, 0, 11)

		Value.Name = "Value"
		Value.Parent = Slider
		Value.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Value.BackgroundTransparency = 1.000
		Value.BorderSizePixel = 0
		Value.Position = UDim2.new(0.868421078, 0, 0.272727281, 0)
		Value.Size = UDim2.new(0, 22, 0, 16)
		Value.Font = Enum.Font.Gotham
		Value.TextScaled = true
		Value.Text = "100"
		Value.TextColor3 = Color3.fromRGB(186, 186, 186)
		Value.TextSize = 12.000
		Value.TextWrapped = true
		Value.TextXAlignment = Enum.TextXAlignment.Left
		updateSize(49)
		local p = math.floor((defaultvalue/maxvalue)*184)
		print(p)
		TheSlider.Size = UDim2.new(0, p, 0, 11)
		Value.Text = defaultvalue
		Back.InputBegan:connect(function(a, b)
			if not b then
				if a.UserInputType == Enum.UserInputType.MouseButton1 then
					value = math.floor((((tonumber(maxvalue) - tonumber(minvalue)) / 185) * TheSlider.AbsoluteSize.X) + tonumber(minvalue)) or 0
					pcall(function()
						callback(value)
					end)
					TheSlider:TweenSize(UDim2.new(0, math.clamp(mouse.X - TheSlider.AbsolutePosition.X, 0, 185), 0, 11), "Out", "Quad", .1, true)
					moveconnection = mouse.Move:Connect(function()
						Value.Text = value
						value = math.floor((((tonumber(maxvalue) - tonumber(minvalue)) / 185) * TheSlider.AbsoluteSize.X) + tonumber(minvalue))
						pcall(function()
							callback(value)
						end)
						TheSlider:TweenSize(UDim2.new(0, math.clamp(mouse.X - TheSlider.AbsolutePosition.X, 0, 185), 0, 11), "Out", "Quad", .1, true)
					end)
					releaseconnection = uis.InputEnded:Connect(function(Mouse)
						if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
							value = math.floor((((tonumber(maxvalue) - tonumber(minvalue)) / 185) * TheSlider.AbsoluteSize.X) + tonumber(minvalue))
							pcall(function()
								callback(value)
							end)
							TheSlider.Size = UDim2.new(0, math.clamp(mouse.X - TheSlider.AbsolutePosition.X, 0, 185), 0, 11)
							moveconnection:Disconnect()
							releaseconnection:Disconnect()
						end
					end)
				end
			end
		end)
	end

	function creator:Button(name, tab, callback)
		name = name or "Button"
		tab = string.upper(tab) or "TAB"
		callback = callback or function() end

		local Button = Instance.new("Frame")
		local Back = Instance.new("Frame")
		local TheCircleThingy = Instance.new("Frame")
		local UICorner = Instance.new("UICorner")
		local Name = Instance.new("TextLabel")

		Button.Name = "Button"
		Button.Parent = Tabs[tab]["Holder"]["Frame"]
		Button.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
		Button.BorderSizePixel = 0
		Button.Size = UDim2.new(0, 190, 0, 28)

		Back.Name = "Back"
		Back.Parent = Button
		Back.BackgroundColor3 = Color3.fromRGB(0, 132, 255)
		Back.BorderSizePixel = 0
		Back.Position = UDim2.new(0, 153, 0, 14)
		Back.Size = UDim2.new(0, 66, 0, 22)
		Back.ClipsDescendants = true
		Back.AnchorPoint = Vector2.new(0.5, 0.5)

		TheCircleThingy.Name = "TheCircleThingy"
		TheCircleThingy.Parent = Back
		TheCircleThingy.AnchorPoint = Vector2.new(0.5, 0.5)
		TheCircleThingy.BackgroundColor3 = Color3.fromRGB(150, 190, 255)
		TheCircleThingy.BorderSizePixel = 0
		TheCircleThingy.Position = UDim2.new(0.5, 0, 0.5, 0)

		UICorner.CornerRadius = UDim.new(32131, 31231)
		UICorner.Parent = TheCircleThingy

		Name.Name = "Name"
		Name.Parent = Button
		Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Name.BackgroundTransparency = 1.000
		Name.BorderSizePixel = 0
		Name.Position = UDim2.new(0.0157894734, 0, 0, 0)
		Name.Size = UDim2.new(0, 154, 0, 28)
		Name.Font = Enum.Font.Gotham
		Name.Text = name
		Name.TextColor3 = Color3.fromRGB(186, 186, 186)
		Name.TextSize = 14.000
		Name.TextWrapped = true
		Name.TextXAlignment = Enum.TextXAlignment.Left
		updateSize(33)
		Back.InputBegan:Connect(function(a, b)
			if not b then
				if a.UserInputType == Enum.UserInputType.MouseButton1 then
					pcall(callback)
					local goal = {}
					goal.Transparency = 1
					goal.Size = UDim2.new(0, 100, 0, 100)
					local ti = TweenInfo.new(.2)
					local tween = game:GetService("TweenService"):Create(TheCircleThingy, ti, goal)
					local tween2 = game:GetService("TweenService"):Create(Back, TweenInfo.new(.1, Enum.EasingStyle.Quint, Enum.EasingDirection.Out), {Size = UDim2.new(0, 69, 0, 25)})
					tween:Play()
					tween2:Play()
					tween.Completed:connect(function()
						TheCircleThingy.BackgroundTransparency = 0
						TheCircleThingy.Size = UDim2.new(0, 0,0,0)
					end)
					tween2.Completed:connect(function()
						Back:TweenSize(UDim2.new(0, 66, 0, 22), "Out", "Quint", .1)
					end)
				end
			end
		end)
	end
	return creator
	
end

return library
