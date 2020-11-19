for i,v in next, game.CoreGui:GetChildren() do
    if v:FindFirstChild("UILIB") then
        v:Remove()
    end
end

local library = {}

local ts = game:GetService("TweenService")
local ti = function(length) 
	return TweenInfo.new(length or 0.2, Enum.EasingStyle.Sine, Enum.EasingDirection.Out)
end
local mouse = game:GetService("Players").LocalPlayer:GetMouse()
local is = game:GetService("UserInputService")
local rs = game:GetService("RunService")

togglefalse = nil
toggletrue = nil

library.topbar = Color3.fromRGB(11, 11, 11)
library.buttoncontainer = Color3.fromRGB(33, 33, 33)
library.mainframe = Color3.fromRGB(22, 22, 22)
library.searchbar = Color3.fromRGB(38, 38, 38)
library.buttoncontainerhovered = Color3.fromRGB(44, 44, 44)
library.toggletrue = toggletrue or Color3.fromRGB(80, 225, 120)
library.togglefalse = togglefalse or Color3.fromRGB(200, 70, 70)
library.scrollbar = Color3.fromRGB(77, 77, 77)
library.dropdowncontainer = Color3.fromRGB(22, 22, 22)
library.divider = Color3.fromRGB(33, 33, 33)
library.descriptiontext = Color3.fromRGB(170, 170, 170)
library.slidingbar = Color3.fromRGB(66, 66, 66)

function library:addRound(object)
	local round = Instance.new("UICorner", object)
	round.CornerRadius = UDim.new(0, 4)
end

function library:Create(name, size)
	name = name or "UILibrary"
	size = size or UDim2.new(0, 400, 0, 450)
	local UILIB = Instance.new("ScreenGui")
	UILIB.Name = game:GetService("HttpService"):GenerateGUID(true)
	UILIB.Parent = game.CoreGui
    UILIB.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    UILIB.ResetOnSpawn = false
	local MainFrame = Instance.new("Frame")
	MainFrame.Name = "UILIB"
	MainFrame.Parent = UILIB
	MainFrame.AnchorPoint = Vector2.new(0.5, 0.5)
	MainFrame.BackgroundColor3 = library.mainframe
	MainFrame.Position = UDim2.new(0.5, 0, 0.5, 0)
	MainFrame.Size = size

	local shadow = Instance.new("ImageLabel")
	shadow.Name = "Shadow"
	shadow.AnchorPoint = Vector2.new(0.5, 0.5)
	shadow.BackgroundTransparency = 1
	shadow.Position = UDim2.new(0.5, 0, 0.5, 0)
	shadow.Size = UDim2.new(1, 12, 1, 12)
	shadow.ImageTransparency = 0.5
	shadow.Image = "rbxassetid://1316045217"
	shadow.ImageColor3 = Color3.fromRGB(22, 22, 22)
	shadow.ScaleType = Enum.ScaleType.Slice
	shadow.SliceCenter = Rect.new(10, 10, 118, 118)
	shadow.Parent = MainFrame

	is.InputBegan:connect(function(input)
		if input.KeyCode == Enum.KeyCode.RightShift then
			MainFrame.Visible = not MainFrame.Visible
		end
	end)

	local s, event = pcall(function()
		return MainFrame.MouseEnter
	end)

	if s then
		MainFrame.Active = true;

		event:connect(function()
			local input = MainFrame.InputBegan:connect(function(key)
				if key.UserInputType == Enum.UserInputType.MouseButton1 then
					local objectPosition = Vector2.new(mouse.X - MainFrame.AbsolutePosition.X, mouse.Y - MainFrame.AbsolutePosition.Y)
					while rs.RenderStepped:wait() and is:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
						MainFrame:TweenPosition(UDim2.new(0, mouse.X - objectPosition.X + (MainFrame.Size.X.Offset * MainFrame.AnchorPoint.X), 0, mouse.Y - objectPosition.Y + (MainFrame.Size.Y.Offset * MainFrame.AnchorPoint.Y)), 'Out', 'Quad', 0.05, true)
					end
				end
			end)

			local leave
			leave = MainFrame.MouseLeave:connect(function()
				input:disconnect()
				leave:disconnect()
			end)
		end)
	end

	library:addRound(MainFrame)

	local Topbar = Instance.new("Frame")
	Topbar.Name = "Topbar"
	Topbar.Parent = MainFrame
	Topbar.BackgroundColor3 = library.topbar
	Topbar.BorderSizePixel = 0
	Topbar.Size = UDim2.new(1, 0, 0, 25)
	
	library:addRound(Topbar)

	local CloseUI = Instance.new("ImageButton")
	CloseUI.Parent = Topbar
	CloseUI.AnchorPoint = Vector2.new(1, 0.5)
	CloseUI.Position = UDim2.new(1, 0, 0.5, 0)
	CloseUI.Image = "http://www.roblox.com/asset/?id=5840446794"
	CloseUI.BackgroundTransparency = 1
	CloseUI.Size = UDim2.new(0, 25, 0, 25)
	CloseUI.ImageColor3 = Color3.fromRGB(255, 255, 255)
	CloseUI.ZIndex = 2
	CloseUI.MouseEnter:connect(function()
		CloseUI.Size = UDim2.new(0, 27, 0, 27)
		CloseUI.Position = UDim2.new(1, 1, 0.5, 0)
	end)
	CloseUI.MouseLeave:connect(function()
		CloseUI.Size = UDim2.new(0, 25, 0, 25)
		CloseUI.Position = UDim2.new(1, 0, 0.5, 0)
	end)
	CloseUI.MouseButton1Click:connect(function()
		UILIB:Destroy()
		UILIB = nil
	end)

	local TextLabel = Instance.new("TextLabel")
	TextLabel.Parent = Topbar
	TextLabel.BackgroundTransparency = 1
	TextLabel.Size = UDim2.new(1, 0, 1, 0)
	TextLabel.Font = Enum.Font.SourceSansSemibold
	TextLabel.TextColor3 = Color3.new(1, 1, 1)
	TextLabel.TextSize = 20
	TextLabel.Text = name

	local Searchframe = Instance.new("Frame")
	Searchframe.Name = "Searchframe"
	Searchframe.Parent = MainFrame
	Searchframe.BackgroundTransparency = 1
	Searchframe.Position = UDim2.new(0, 0, 0, 25)
	Searchframe.Size = UDim2.new(1, 0, 0, 20)

	local Search = Instance.new("TextBox")
	Search.Name = "Search"
	Search.Parent = Searchframe
	Search.BackgroundColor3 = library.searchbar
	Search.BorderSizePixel = 0
	Search.Size = UDim2.new(1, 0, 1, 0)
	Search.Font = Enum.Font.SourceSansSemibold
	Search.PlaceholderColor3 = Color3.new(0.698039, 0.698039, 0.698039)
	Search.PlaceholderText = "Search"
	Search.Text = ""
	Search.TextColor3 = Color3.new(0, 0, 0)
	Search.TextSize = 16
	Search.TextColor3 = Color3.fromRGB(200, 200, 200)

	local Container = Instance.new("ScrollingFrame")
	Container.Name = "Container"
	Container.Parent = MainFrame
	Container.BackgroundColor3 = Color3.new(1, 1, 1)
	Container.BackgroundTransparency = 1
	Container.Position = UDim2.new(0, 0, 0, 45)
	Container.Size = UDim2.new(1, 0, 1, -45)
	Container.CanvasSize = UDim2.new(1, 0, 1, 0)
	Container.ScrollBarThickness = 2
	Container.ScrollingDirection = Enum.ScrollingDirection.Y
	Container.ScrollBarImageColor3 = library.scrollbar
	Container.BorderSizePixel = 0
	Container.TopImage = "rbxassetid://967852042"
	Container.MidImage = "rbxassetid://967852042"
	Container.BottomImage = "rbxassetid://967852042"

	local UIListLayout = Instance.new("UIListLayout")
	UIListLayout.Parent = Container
	UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIListLayout.Padding = UDim.new(0, 10)

	local function updatescroll()
		Container.CanvasSize = UDim2.new(0, 0, 0, UIListLayout.AbsoluteContentSize.Y + 20)
	end

	local UIPadding = Instance.new("UIPadding")
	UIPadding.Parent = Container
	UIPadding.PaddingTop = UDim.new(0, 10)

	Search.Changed:connect(function(text)
		updatescroll()
		local text = Search.Text:lower()
		if text ~= "" then
			for _, button in next, Container:GetChildren() do
				if button:IsA("TextButton") then
					if string.find(button.Description.Text:lower(), text) or string.find(button.ButtonName.Text:lower(), text) then
						button.Visible = true
					else
						button.Visible = false
					end
				end
			end
		else
			for _, button in next, Container:GetChildren() do
				if button:IsA("TextButton") then
					button.Visible = true
				end
			end
		end
	end)

	local features = {}

	function features:Divider(name)
		name = name or "Divider"

		local Divider = Instance.new("TextLabel")
		Divider.Size = UDim2.new(1, 0, 0, 20)
		Divider.BorderSizePixel = 0
		Divider.Parent = Container
		Divider.BackgroundColor3 = library.divider
		Divider.Font = Enum.Font.SourceSansSemibold
		Divider.Text = name
		Divider.TextColor3 = Color3.new(1, 1, 1)
		Divider.TextSize = 16
	end

	function features:Button(name, description, callback)
		name = name or "Button"
		description = description or "Button's description"
		callback = callback or function() end

		local ButtonContainer = Instance.new("TextButton")
		ButtonContainer.Name = "Button"
		ButtonContainer.Parent = Container
		ButtonContainer.BackgroundColor3 = library.buttoncontainer
		ButtonContainer.BorderSizePixel = 0
		ButtonContainer.Size = UDim2.new(1, -20, 0, 50)
		ButtonContainer.Text = ""
		ButtonContainer.AutoButtonColor = false

		library:addRound(ButtonContainer)

		local Buttonname = Instance.new("TextLabel")
		Buttonname.Name = "ButtonName"
		Buttonname.Parent = ButtonContainer
		Buttonname.BackgroundColor3 = Color3.new(1, 1, 1)
		Buttonname.BackgroundTransparency = 1
		Buttonname.Position = UDim2.new(0, 10, 0, 0)
		Buttonname.Size = UDim2.new(0.5, 0, 0.5, 0)
		Buttonname.Font = Enum.Font.SourceSansSemibold
		Buttonname.Text = name
		Buttonname.TextColor3 = Color3.new(1, 1, 1)
		Buttonname.TextSize = 16
		Buttonname.TextXAlignment = Enum.TextXAlignment.Left

		local Buttondescription = Instance.new("TextLabel")
		Buttondescription.Name = "Description"
		Buttondescription.Parent = ButtonContainer
		Buttondescription.AnchorPoint = Vector2.new(0, 1)
		Buttondescription.BackgroundColor3 = Color3.new(1, 1, 1)
		Buttondescription.BackgroundTransparency = 1
		Buttondescription.Position = UDim2.new(0, 10, 1, 0)
		Buttondescription.Size = UDim2.new(0.5, 0, 0.5, 0)
		Buttondescription.Font = Enum.Font.SourceSansSemibold
		Buttondescription.Text = description
		Buttondescription.TextColor3 = library.descriptiontext
		Buttondescription.TextSize = 15
		Buttondescription.TextXAlignment = Enum.TextXAlignment.Left
		Buttondescription.TextYAlignment = Enum.TextYAlignment.Top

		local Button = Instance.new("Frame")
		Button.Name = "Button"
		Button.Parent = ButtonContainer
		Button.AnchorPoint = Vector2.new(1, 0)
		Button.BackgroundColor3 = Color3.fromRGB(50, 70, 200)
		Button.Position = UDim2.new(1, -5, 0, 5)
		Button.Size = UDim2.new(0, 40, 0, 40)
		Button.BackgroundTransparency = 1

		local Click = Instance.new("ImageLabel")
		Click.Parent = Button
		Click.BackgroundTransparency = 1
		Click.Size = UDim2.new(1, 0, 1, 0)
		Click.Image = "http://www.roblox.com/asset/?id=5837528348"

		ButtonContainer.MouseButton1Click:connect(function()
			spawn(function()
				pcall(callback)
			end)
		end)

		local hovered = ts:Create(ButtonContainer, ti(0.2), {BackgroundColor3 = library.buttoncontainerhovered})
		local normal = ts:Create(ButtonContainer, ti(0.2), {BackgroundColor3 = library.buttoncontainer})

		ButtonContainer.MouseEnter:connect(function()
			hovered:Play()
		end)

		ButtonContainer.MouseLeave:connect(function()
			normal:Play()
		end)
		updatescroll()
	end

	function features:Toggle(name, description, state, callback)
		name = name or "Toggle"
		description = description or "Toggle's description"
		local state = state or false
		callback = callback or function() end

		local ToggleContainer = Instance.new("TextButton")
		ToggleContainer.Name = "Toggle"
		ToggleContainer.Parent = Container
		ToggleContainer.BackgroundColor3 = library.buttoncontainer
		ToggleContainer.BorderSizePixel = 0
		ToggleContainer.Size = UDim2.new(1, -20, 0, 50)
		ToggleContainer.AutoButtonColor = false
		ToggleContainer.Text = ""

		library:addRound(ToggleContainer)

		local ButtonName = Instance.new("TextLabel")
		ButtonName.Name = "ButtonName"
		ButtonName.Parent = ToggleContainer
		ButtonName.BackgroundColor3 = Color3.new(1, 1, 1)
		ButtonName.BackgroundTransparency = 1
		ButtonName.Position = UDim2.new(0, 10, 0, 0)
		ButtonName.Size = UDim2.new(0.5, 0, 0.5, 0)
		ButtonName.Font = Enum.Font.SourceSansSemibold
		ButtonName.Text = name
		ButtonName.TextColor3 = Color3.new(1, 1, 1)
		ButtonName.TextSize = 16
		ButtonName.TextXAlignment = Enum.TextXAlignment.Left

		local Description = Instance.new("TextLabel")
		Description.Name = "Description"
		Description.Parent = ToggleContainer
		Description.AnchorPoint = Vector2.new(0, 1)
		Description.BackgroundColor3 = Color3.new(1, 1, 1)
		Description.BackgroundTransparency = 1
		Description.Position = UDim2.new(0, 10, 1, 0)
		Description.Size = UDim2.new(0.5, 0, 0.5, 0)
		Description.Font = Enum.Font.SourceSansSemibold
		Description.Text = description
		Description.TextColor3 = library.descriptiontext
		Description.TextSize = 15
		Description.TextXAlignment = Enum.TextXAlignment.Left
		Description.TextYAlignment = Enum.TextYAlignment.Top

		local Colour = Instance.new("Frame")
		Colour.Name = "Colour"
		Colour.Parent = ToggleContainer
		Colour.AnchorPoint = Vector2.new(1, 0)
		Colour.BackgroundColor3 = state and library.toggletrue or library.togglefalse
		Colour.Position = UDim2.new(1, -5, 0, 5)
		Colour.Size = UDim2.new(0, 40, 0, 20)

		library:addRound(Colour)

		local Sliding = Instance.new("Frame")
		Sliding.Parent = Colour
		Sliding.AnchorPoint = Vector2.new(0, 0.5)
		Sliding.BackgroundColor3 = Color3.new(1, 1, 1)
		Sliding.Position = state and UDim2.new(1, -20, 0.5, 0) or UDim2.new(0, 0, 0.5, 0)
		Sliding.Size = UDim2.new(0.5, 0, 1, 0)
		Sliding.ZIndex = 2

		library:addRound(Sliding)

		local slidingtofalse = ts:Create(Sliding, ti(0.2), {Position = UDim2.new(0, 0, 0.5, 0)})
		local colourtofalse = ts:Create(Colour, ti(0.2), {BackgroundColor3 = library.togglefalse})
		local slidingtotrue = ts:Create(Sliding, ti(0.2), {Position = UDim2.new(1, -20, 0.5, 0)})
		local colourtotrue = ts:Create(Colour, ti(0.2), {BackgroundColor3 = library.toggletrue})
		local hovered = ts:Create(ToggleContainer, ti(0.2), {BackgroundColor3 = library.buttoncontainerhovered})
		local normal = ts:Create(ToggleContainer, ti(0.2), {BackgroundColor3 = library.buttoncontainer})

		ToggleContainer.MouseButton1Click:connect(function()
			state = not state
			spawn(function()
				pcall(callback, state)
			end)
			if state then
				slidingtotrue:Play()
				colourtotrue:Play()
			else
				slidingtofalse:Play()
				colourtofalse:Play()
			end
		end)

		ToggleContainer.MouseEnter:connect(function()
			hovered:Play()
		end)

		ToggleContainer.MouseLeave:connect(function()
			normal:Play()
		end)
		updatescroll()
	end

	function features:Dropdown(name, description, options, callback)
		name = name or "Dropdown"
		description = description or ""
		options = options or {"#1", "#2", "#3"}
		callback = callback or function() end
		local state = false
		local Dropdown = Instance.new("TextButton")
		Dropdown.Name = "Dropdown"
		Dropdown.Parent = Container
		Dropdown.BackgroundColor3 = library.buttoncontainer
		Dropdown.BorderSizePixel = 0
		Dropdown.Size = UDim2.new(1, -20, 0, 50)
		Dropdown.AutoButtonColor = false
		Dropdown.Text = ""
		
		library:addRound(Dropdown)
		
		local ButtonName = Instance.new("TextLabel")
		ButtonName.Name = "ButtonName"
		ButtonName.Parent = Dropdown
		ButtonName.BackgroundTransparency = 1
		ButtonName.Position = UDim2.new(0, 10, 0, 0)
		ButtonName.Size = UDim2.new(0.5, 0, 0, 25)
		ButtonName.Font = Enum.Font.SourceSansSemibold
		ButtonName.Text = name
		ButtonName.TextColor3 = Color3.fromRGB(255, 255, 255)
		ButtonName.TextSize = 16
		ButtonName.TextXAlignment = Enum.TextXAlignment.Left

		local Description = Instance.new("TextLabel")
		Description.Name = "Description"
		Description.Parent = Dropdown
		Description.AnchorPoint = Vector2.new(0, 1)
		Description.BackgroundTransparency = 1
		Description.Position = UDim2.new(0, 10, 0, 50)
		Description.Size = UDim2.new(0.5, 0, 0, 25)
		Description.Font = Enum.Font.SourceSansSemibold
		Description.Text = description
		Description.TextColor3 = library.descriptiontext
		Description.TextSize = 15
		Description.TextXAlignment = Enum.TextXAlignment.Left
		Description.TextYAlignment = Enum.TextYAlignment.Top

		local Button = Instance.new("Frame")
		Button.Name = "Button"
		Button.Parent = Dropdown
		Button.AnchorPoint = Vector2.new(1, 0)
		Button.BackgroundTransparency = 1
		Button.Position = UDim2.new(1, -5, 0, 5)
		Button.Size = UDim2.new(0, 40, 0, 40)

		local ImageLabel = Instance.new("ImageLabel")
		ImageLabel.Parent = Button
		ImageLabel.BackgroundTransparency = 1
		ImageLabel.Size = UDim2.new(1, 0, 1, 0)
		ImageLabel.Rotation = 90
		ImageLabel.Image = "http://www.roblox.com/asset/?id=5844057859"

		local OptionsContainer = Instance.new("Frame")
		OptionsContainer.Name = "Options Container"
		OptionsContainer.Parent = Dropdown
		OptionsContainer.AnchorPoint = Vector2.new(0.5, 0)
		OptionsContainer.BackgroundColor3 = library.dropdowncontainer
		OptionsContainer.Position = UDim2.new(0.5, 0, 0, 55)
		OptionsContainer.Size = UDim2.new(1, -10, 1, -60)
		OptionsContainer.ClipsDescendants = true
		OptionsContainer.Visible = false
		
		library:addRound(OptionsContainer)

		local DropdownListLayout = Instance.new("UIListLayout")
		DropdownListLayout.Parent = OptionsContainer
		DropdownListLayout.SortOrder = Enum.SortOrder.LayoutOrder

		for i, v in next, options do

			if i ~= 1 then
				local Divider = Instance.new("Frame")
				Divider.Name = "Divider"
				Divider.Parent = OptionsContainer
				Divider.BackgroundColor3 = library.buttoncontainer
				Divider.BorderSizePixel = 0
				Divider.Size = UDim2.new(1, 0, 0, 2)
				
				local hovered = ts:Create(Divider, ti(0.2), {BackgroundColor3 = library.buttoncontainerhovered})
				local normal = ts:Create(Divider, ti(0.2), {BackgroundColor3 = library.buttoncontainer})

				Dropdown.MouseEnter:connect(function()
					hovered:Play()
				end)

				Dropdown.MouseLeave:connect(function()
					normal:Play()
				end)
			end

			local Option = Instance.new("TextButton")
			Option.Name = "Option"
			Option.Parent = OptionsContainer
			Option.BackgroundTransparency = 1
			Option.Size = UDim2.new(1, 0, 0, 25)
			Option.Font = Enum.Font.SourceSans
			Option.Text = ""
			Option.TextColor3 = Color3.new(0, 0, 0)
			Option.TextSize = 14

			local TextLabel = Instance.new("TextLabel")
			TextLabel.Parent = Option
			TextLabel.AnchorPoint = Vector2.new(0.5, 0.5)
			TextLabel.BackgroundTransparency = 1
			TextLabel.Position = UDim2.new(0.5, 0, 0.5, 0)
			TextLabel.Size = UDim2.new(1, -12, 1, 0)
			TextLabel.Font = Enum.Font.SourceSansSemibold
			TextLabel.TextColor3 = library.descriptiontext
			TextLabel.TextSize = 15
			TextLabel.Text = tostring(v)
			TextLabel.TextXAlignment = Enum.TextXAlignment.Left

			Option.MouseButton1Click:connect(function()
				spawn(function()
					callback(v)
				end)
			end)			
		end
		
		local hovered = ts:Create(Dropdown, ti(0.2), {BackgroundColor3 = library.buttoncontainerhovered})
		local normal = ts:Create(Dropdown, ti(0.2), {BackgroundColor3 = library.buttoncontainer})

		Dropdown.MouseEnter:connect(function()
			hovered:Play()
		end)

		Dropdown.MouseLeave:connect(function()
			normal:Play()
		end)
		
		Dropdown.MouseButton1Click:connect(function()
			spawn(function()
				state = not state
				ts:Create(ImageLabel, ti(0.2), {Rotation = state and 0 or 90}):Play()
				local DropdownTween = ts:Create(Dropdown, ti(0.2), {Size = UDim2.new(1, -20, 0, state and DropdownListLayout.AbsoluteContentSize.Y + 60 or 50)})
				DropdownTween:Play()
				spawn(function()
					while DropdownTween.PlaybackState ~=  Enum.PlaybackState.Completed and rs.RenderStepped:wait() do
						if Dropdown.Size.Y.Offset < 60 and not state then
							OptionsContainer.Visible = false
						end
						if Dropdown.Size.Y.Offset > 60 and state then
							OptionsContainer.Visible = true
						end
						updatescroll()
					end
					OptionsContainer.Visible = state
				end)
			end)
		end)
		
        updatescroll()
        
        local mt = {
			__newindex = function(d, i, v)
				print(d, i, v)
				if i == "Description" then
					Description.Text = v            
				end
			end
		}
		local dropdownlib = {}
		setmetatable(dropdownlib, mt)
        return dropdownlib
	end
	
	function features:Slider(name, description, min, max, default, callback)
		name = name or "Slider"
		description = description or ""
		min = min or 0
		max = max or 100
		default = default or max / 2 or 50
		callback = callback or function() end
			
		local Slider = Instance.new("TextButton")
		Slider.Name = "Slider"
		Slider.Parent = Container
		Slider.BackgroundColor3 = library.buttoncontainer
		Slider.BorderSizePixel = 0
		Slider.Size = UDim2.new(1, -20, 0, 50)
		Slider.AutoButtonColor = false
		Slider.Text = ""
		
		library:addRound(Slider)
		
		local ButtonName = Instance.new("TextLabel")
		ButtonName.Name = "ButtonName"
		ButtonName.Parent = Slider
		ButtonName.BackgroundColor3 = Color3.new(1, 1, 1)
		ButtonName.BackgroundTransparency = 1
		ButtonName.Position = UDim2.new(0, 10, 0, 0)
		ButtonName.Size = UDim2.new(0.5, 0, 0.5, 0)
		ButtonName.Font = Enum.Font.SourceSansSemibold
		ButtonName.Text = name
		ButtonName.TextColor3 = Color3.new(1, 1, 1)
		ButtonName.TextSize = 16
		ButtonName.TextXAlignment = Enum.TextXAlignment.Left
		
		local Description = Instance.new("TextLabel")
		Description.Name = "Description"
		Description.Parent = Slider
		Description.AnchorPoint = Vector2.new(0, 1)
		Description.BackgroundColor3 = Color3.new(1, 1, 1)
		Description.BackgroundTransparency = 1
		Description.Position = UDim2.new(0, 10, 1, 0)
		Description.Size = UDim2.new(0.5, 0, 0.5, 0)
		Description.Font = Enum.Font.SourceSansSemibold
		Description.Text = description
		Description.TextColor3 = library.descriptiontext
		Description.TextSize = 15
		Description.TextXAlignment = Enum.TextXAlignment.Left
		Description.TextYAlignment = Enum.TextYAlignment.Top
		
		local Sliding = Instance.new("TextLabel")
		Sliding.Name = "Sliding"
		Sliding.Parent = Slider
		Sliding.AnchorPoint = Vector2.new(1, 1)
		Sliding.BackgroundColor3 = library.slidingbar
		Sliding.Position = UDim2.new(1, -5, 0.75, 0)
		Sliding.Size = UDim2.new(0.5, 0, 0, 7)
		Sliding.Font = Enum.Font.SourceSans
		Sliding.Text = ""
		Sliding.TextColor3 = Color3.new(0, 0, 0)
		Sliding.TextSize = 14
		
		local slidinground = Instance.new("UICorner", Sliding)
		slidinground.CornerRadius = UDim.new(0, 2)
		
		local Indicator = Instance.new("Frame")
		Indicator.Name = "Indicator"
		Indicator.Parent = Sliding
		Indicator.AnchorPoint = Vector2.new(0.5, 0.5)
		Indicator.BackgroundColor3 = Color3.new(1, 1, 1)
		Indicator.Position = UDim2.new(0, 0, 0.5, 0)
		Indicator.Size = UDim2.new(0, 16, 0, 16)
		
		local indicatorround = Instance.new("UICorner", Indicator)
		slidinground.CornerRadius = UDim.new(0, 100)
		
		local Value = Instance.new("TextLabel")
		Value.Name = "Value"
		Value.Parent = Slider
		Value.AnchorPoint = Vector2.new(1, 1)
		Value.BackgroundTransparency = 1
		Value.Position = UDim2.new(1, -5, 0.5, 0)
		Value.Size = UDim2.new(0.5, 0, 0.5, 0)
		Value.Font = Enum.Font.SourceSansSemibold
		Value.Text = string.format("%d / %d", default, max)
		Value.TextColor3 = library.descriptiontext
		Value.TextSize = 16
		Value.TextXAlignment = Enum.TextXAlignment.Right
		
		local down
		local percentage = 0
		local value
		
		Slider.MouseButton1Down:connect(function()
			down = true
			while down and rs.RenderStepped:wait() do
				percentage = math.clamp(((mouse.X - Sliding.AbsolutePosition.X) / Sliding.AbsoluteSize.X), 0, 1)
				Indicator:TweenPosition(UDim2.new(percentage, 0, 0.5, 0), Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 0.05)
				value = (percentage * (max - min)) + min
				Value.Text = string.format("%d / %d", value, max)
				spawn(function()
					pcall(callback, math.floor(value))
				end)
			end
		end)
		
		connection = is.InputEnded:connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 and UILIB then
				down = false
				Indicator:TweenPosition(UDim2.new(percentage, 0, 0.5, 0), Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 0.02) 
			elseif not UILIB then
				connection:Disconnect()
			end
		end)
		
		local hovered = ts:Create(Slider, ti(0.2), {BackgroundColor3 = library.buttoncontainerhovered})
		local normal = ts:Create(Slider, ti(0.2), {BackgroundColor3 = library.buttoncontainer})

		Slider.MouseEnter:connect(function()
			hovered:Play()
		end)

		Slider.MouseLeave:connect(function()
			normal:Play()
		end)
		
		updatescroll()
		
		--[[local mt = {
			__newindex = function(d, i, v)
				print(d, i, v)
				if i == "Name" then
					ButtonName.Text = v
				elseif i == "Description" then
					Description.Text = v
				elseif i == "Min" then
					min = v
				elseif i == "Max" then
					max = v				
				end
			end
		}
		local sliderlib = {}
		setmetatable(sliderlib, mt)
		return sliderlib]]
	end
	return features
end
return library
