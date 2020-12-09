--[[
        UI LIBRARY MADE BY LITTEN/0866
https://v3rmillion.net/member.php?action=profile&uid=70461
--]]

if not getgenv().require then
	getgenv().require = require
end

--// API References
local GUIData = (function()
	-- Variables
	_V = 1.3
	
	local screenGui = (script:FindFirstChild("ScreenGui")) or game:GetObjects("rbxassetid://5646585230")[1]:FindFirstChild("ScreenGui", true)
	  local Container = screenGui.Frame
	    local Opt = Container.OptionsFrame
	    local Checkbox = Opt.Checkbox
	    local Color = Opt.Color
	    local Frame = Opt.Frame
	    local Execute = Opt.Execute
	    local Mode = Opt.Mode
	    local Number = Opt.Number
	    local Toggle = Opt.Toggle
	  local Mods = screenGui.Mods
	    local ModLabel = Mods.Example
	
	local TextService = game:GetService("TextService")
	local UserInputService = game:GetService("UserInputService")
	local HttpService = game:GetService("HttpService")
	local Player = game:GetService("Players").LocalPlayer
	  local Mouse = Player:GetMouse()
	
	pcall(function()
		screenGui.Parent = game:GetService("CoreGui")
	end)
	
	Container.Parent = nil
	Checkbox.Parent = nil
	Color.Parent = nil
	Frame.Parent = nil
	Execute.Parent = nil
	Mode.Parent = nil
	Number.Parent = nil
	Toggle.Parent = nil
	ModLabel.Parent = nil
	
	local settingsArray = {{Object = screenGui},{}}
	local saveData = {Options = {}, Hotkeys = {}}
	
	local hotkeyFunctions = {}
	local gui = {}
	
	-- Color Functions
	local color = {}
	local colors = {
		TextDisabled = Color3.fromRGB(200, 200, 200),
		TextEnabled = Color3.fromRGB(255, 255, 255),
	}
	
	local Colors = {
		Color3.fromRGB(255, 73, 73),
		Color3.fromRGB(255, 161, 66),
		Color3.fromRGB(255, 233, 62),
		Color3.fromRGB(137, 255, 64),
		Color3.fromRGB(64, 255, 140),
		Color3.fromRGB(66, 252, 255),
		Color3.fromRGB(64, 147, 255),
		Color3.fromRGB(255, 93, 253),
		Color3.fromRGB(195, 110, 255),
		Color3.fromRGB(255, 90, 134),
		Color3.fromRGB(255, 255, 255),
		Color3.fromRGB(209, 209, 209),
	}
	
	local function h2rgb(m1, m2, h)
		if h<0 then h = h+1 end
		if h>1 then h = h-1 end
		if h*6<1 then
			return m1+(m2-m1)*h*6
		elseif h*2<1 then
			return m2
		elseif h*3<2 then
			return m1+(m2-m1)*(2/3-h)*6
		else
			return m1
		end
	end
	
	function color:rgbToHsv(r, g, b)
		local a = 0
		r, g, b, a = r / 255, g / 255, b / 255, a / 255
		local max, min = math.max(r, g, b), math.min(r, g, b)
		local h, s, v
		v = max
	
		local d = max - min
		if max == 0 then s = 0 else s = d / max end
	
		if max == min then
			h = 0 -- achromatic
		else
			if max == r then
			h = (g - b) / d
			if g < b then h = h + 6 end
			elseif max == g then h = (b - r) / d + 2
			elseif max == b then h = (r - g) / d + 4
			end
			h = h / 6
		end
	
		return h, s, v
	end
	
	function color:hslToRgb(h, s, L)
		h = h / 360
		local m2 = L <= .5 and L*(s+1) or L+s-L*s
		local m1 = L*2-m2
		return
			h2rgb(m1, m2, h+1/3),
			h2rgb(m1, m2, h),
			h2rgb(m1, m2, h-1/3)
	end
	
	function color:rgbToHsl(r, g, b)
		local min = math.min(r, g, b)
		local max = math.max(r, g, b)
		local delta = max - min
	
		local h, s, l = 0, 0, (min + max) / 2
	
		if l > 0 and l < 0.5 then s = delta / (max + min) end
		if l >= 0.5 and l < 1 then s = delta / (2 - max - min) end
	
		if delta > 0 then
			if max == r and max ~= g then h = h + (g-b) / delta end
			if max == g and max ~= b then h = h + 2 + (b-r) / delta end
			if max == b and max ~= r then h = h + 4 + (r-g) / delta end
			h = h / 6
		end
	
		if h < 0 then h = h + 1 end
		if h > 1 then h = h - 1 end
	
		return h * 360, s, l
	end
	
	function color:adjustLightness(color3, amount)
		local h, s, l = self:rgbToHsl(color3.r, color3.g, color3.b)
		return Color3.new(self:hslToRgb(h, s, l + amount))
	end
	
	-- UI Functions
	function gui.tween(object,style,direction,t,goal)
	    local tweenservice = game:GetService("TweenService")
	    local tweenInfo = TweenInfo.new(t,Enum.EasingStyle[style],Enum.EasingDirection[direction])
	    local tween = tweenservice:Create(object,tweenInfo,goal)
		tween.Completed:Connect(function()
			tween:Destroy()
		end)
	    tween:Play()
	    return tween
	end
	
	function gui:makeDraggable(ui, callback)
		local UserInputService = game:GetService("UserInputService")
		
		local dragging
		local dragInput
		local dragStart
		local startPos
		
		local function update(input)
			local delta = input.Position - dragStart
			ui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
			
			if callback then
				callback(ui.Position.X.Offset, ui.Position.Y.Offset)
			end
		end
		
		ui.InputBegan:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				dragging = true
				dragStart = input.Position
				startPos = ui.Position
				
				input.Changed:Connect(function()
					if input.UserInputState == Enum.UserInputState.End then
						dragging = false
					end
				end)
			end
		end)
		
		ui.InputChanged:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
				dragInput = input
			end
		end)
		
		UserInputService.InputChanged:Connect(function(input)
			if input == dragInput and dragging then
				update(input)
			end
		end)
	end
	
	function gui:unpack(data, type)
		if data == nil then return end
		if type == "UDim2" then
			return data and UDim2.new(data[1], data[2], data[3], data[4])
		elseif type == "boolean" then
			return data == 1 and true or false
		elseif type == "Color3" then
			return Color3.new(data[1], data[2], data[3])
		end
		return data
	end
	
	function gui:pack(data)
		if typeof(data) == "UDim2" then
			return {data.X.Scale, data.X.Offset, data.Y.Scale, data.Y.Offset}
		elseif typeof(data) == "boolean" then
			return data and 1 or 0
		elseif typeof(data) == "Color3" then
			return {data.r, data.g, data.b}
		end
		return data
	end
	
	function gui:getn(array)
		local n = 0
		for _, v in pairs(array) do
			n = n + 1
		end
		return n
	end
	
	function gui:setText(textLabel, text)
		text = tostring(text)
		textLabel.Text = text
		if textLabel:FindFirstChild("Opaque") then
			textLabel.Opaque.Text = text
		end
		if textLabel:FindFirstChild("Shadow") then
			textLabel.Shadow.Text = text
		end
	end
	
	function gui:onDoubleTap(guiObject, callback)
		local lastTap = tick()
		guiObject.InputBegan:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 then
				if tick() - lastTap < 0.25 then
					callback()
				end
				lastTap = tick()
			end
		end)
	end
	
	local connections = {}
	function gui:connect(func)
		table.insert(connections, func)
	end
	
	function gui:createList(guiObject, guiData)
		local ListLayout = guiObject.OptionsFrame.UIListLayout
		local Padding = guiObject.OptionsFrame.UIPadding
		guiObject.OptionsFrame.UIListLayout.Changed:Connect(function(Property)
			if Property == "AbsoluteContentSize" then
				guiData.ySize = ListLayout.AbsoluteContentSize.Y + 2 + Padding.PaddingTop.Offset + ListLayout.Padding.Offset * 2
			end
		end)
		
		gui:connect(function()
			if guiObject:FindFirstChild("Title") then
				local yRes = Mouse.ViewSizeY
				local diff = yRes - (guiData.yPos + guiData.ySize)
				local difference = math.clamp(diff, 0, 5000)
				guiObject.OptionsFrame.CanvasSize = UDim2.new(1, 0, 1.001, guiData.ySize - 35)
				
				if guiData.Open then
					guiObject.OptionsFrame.Size = guiObject.OptionsFrame.Size:Lerp(UDim2.new(1, 0, 0, guiData.ySize + math.clamp(diff, -5000, 0)), 0.3)
				else
					guiObject.OptionsFrame.Size = guiObject.OptionsFrame.Size:Lerp(UDim2.new(1, 0, 0, 0), 0.3)
				end
				
				guiObject.Frame.Size = guiObject.OptionsFrame.Size
			else
				if guiData.Open then
					guiObject.Size = guiObject.Size:Lerp(UDim2.new(1, -8, 0, 35 + guiData.ySize), 0.3)
				else
					guiObject.Size = guiObject.Size:Lerp(UDim2.new(1, -8, 0, 35), 0.3)
				end
			end
		end)
		
		if guiObject:FindFirstChild("Dropdown") then
			guiObject.Dropdown.Visible = false
			guiObject.Dropdown.MouseButton1Down:Connect(function()
				guiData.Open = not guiData.Open
				if guiData.Open then
					guiObject.Dropdown.Image = "rbxassetid://3559638428"
				else
					guiObject.Dropdown.Image = "rbxassetid://3554238678"
				end
			end)
		else
			gui:onDoubleTap(guiObject, function()
				guiData.Open = not guiData.Open
			end)
		end
	end
	
	function gui:textColorOnHover(guiObject, guiData)
		local hover = guiData.baseColor or guiObject.TextColor3
		local default = color:adjustLightness(hover, -0.075)
		local mdown = color:adjustLightness(hover, -0.15)
		local mouseIn
		
		local function update()
			if guiData.baseColor then
				hover = guiData.baseColor or guiObject.TextColor3
				default = color:adjustLightness(hover, -0.075)
				mdown = color:adjustLightness(hover, -0.15)
			end
		end
		
		guiObject.MouseEnter:Connect(function()
			update()
			gui.tween(guiObject, "Sine", "Out", 0.25, {
				TextColor3 = hover;
			})
			mouseIn = true
		end)
		
		guiObject.MouseLeave:Connect(function()
			mouseIn = false
			update()
			gui.tween(guiObject, "Sine", "Out", 0.25, {
				TextColor3 = default;
			})
		end)
		
		guiObject.InputBegan:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 then
				update()
				gui.tween(guiObject, "Sine", "Out", 0.25, {
					TextColor3 = mdown;
				})
			end
		end)
		
		guiObject.InputEnded:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 then
				update()
				gui.tween(guiObject, "Sine", "Out", 0.25, {
					TextColor3 = mouseIn and hover or default;
				})
			end
		end)
		
		guiObject.TextColor3 = default
	end
	
	function gui:sliderXY(sliderFrame, inputObjects, callback)
		local inputDown = false
		
		local function refresh(c1, c2)
			local sliderX = sliderFrame.AbsolutePosition.X + sliderFrame.AbsoluteSize.X
			local sliderY = sliderFrame.AbsolutePosition.Y + sliderFrame.AbsoluteSize.Y
			
			local distX = sliderX - Mouse.X
			local distY = sliderY - Mouse.Y
			
			local deltaX = 1-math.clamp(distX / sliderFrame.AbsoluteSize.X, 0, 1)
			local deltaY = 1-math.clamp(distY / sliderFrame.AbsoluteSize.Y, 0, 1)
			
			if callback then
				callback(c1 or deltaX, c2 or deltaY)
			end
		end
		
		for _, obj in pairs(inputObjects) do
			obj.InputBegan:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					inputDown = true
					refresh()
				end
			end)
			obj.InputEnded:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					inputDown = false
					refresh()
				end
			end)
			obj.InputChanged:Connect(function(input)
				if input == nil or input.UserInputType == Enum.UserInputType.MouseMovement then
					if inputDown then
						refresh()
					end
				end
			end)
		end
		
		return refresh
	end
	
	function gui:createSlider(sliderFrame, inputObjects, callback)
		local slider = sliderFrame.Value
		local inputDown = false
		
		local absPos = sliderFrame.AbsolutePosition.X + sliderFrame.AbsoluteSize.X
		local absSize = sliderFrame.AbsoluteSize.X
		
		local function refresh(custom)
			local mouseX = Mouse.X
			local sliderX = absPos
			local dist = sliderX - mouseX
			local delta = 1 - math.clamp(dist / absSize, 0, 1)
			
			if custom then
				delta = custom
			end
			
			slider.Size = UDim2.new(delta, 0, 1, 0)
			if callback then
				callback(delta, custom)
			end
		end
		
		for _, obj in pairs(inputObjects) do
			obj.InputBegan:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					inputDown = true
					absPos = sliderFrame.AbsolutePosition.X + sliderFrame.AbsoluteSize.X
					absSize = sliderFrame.AbsoluteSize.X
					refresh()
				end
			end)
			obj.InputEnded:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					inputDown = false
					refresh()
				end
			end)
			obj.InputChanged:Connect(function(input)
				if input == nil or input.UserInputType == Enum.UserInputType.MouseMovement then
					if inputDown then
						refresh()
					end
				end
			end)
		end
		
		return refresh
	end
	
	function gui:textSize(txt, vSize)
		return TextService:GetTextSize(txt.Text, txt.TextSize, txt.Font, vSize)
	end
	
	local currentHint = 0
	
	function gui:addHint(guiObject, hintText)
		local hintKey = math.random()
		guiObject.MouseEnter:Connect(function()
			hintKey = math.random()
			currentHint = hintKey
			
			wait(1)
			
			if currentHint == hintKey then
				gui:setText(screenGui.Hint, " " .. hintText .. " ")
				local textSize = gui:textSize(screenGui.Hint, Vector2.new(2500, 500))
				screenGui.Hint.Position = UDim2.new(0, Mouse.X, 0, Mouse.Y + 4)
				screenGui.Hint.Size = UDim2.new(0, textSize.X, 0, textSize.Y)
				screenGui.Hint.Visible = true
			end
		end)
		
		guiObject.MouseLeave:Connect(function()
			hintKey = math.random()
		end)
		
		Mouse.Move:Connect(function()
			if currentHint == hintKey then
				screenGui.Hint.Visible = false
			end
		end)
	end
	
	-- UI Type Library
	local lib = {}
	
	function lib.Color(data, dataArray)
		local guiObject = Color:Clone()
		local color3Value = gui:unpack(saveData.Options[data.ID].Value, "Color3") or data.Default or Color3.new(1, 1, 1)
		local guiData = {}
		
		local HSV = color3Value
		local H, S, V = color:rgbToHsv(HSV.r * 255, HSV.g * 255, HSV.b * 255)
		
		local newValue = function()
			HSV = Color3.fromHSV(H, S, V)
			guiObject.SV.BackgroundColor3 = Color3.fromHSV(H, 1, 1)
			guiObject.Indicator.BackgroundColor3 = HSV
			saveData.Options[data.ID].Value = gui:pack(HSV, "Color3")
			
			guiObject.R.Text = math.floor(HSV.r * 255)
			guiObject.G.Text = math.floor(HSV.g * 255)
			guiObject.B.Text = math.floor(HSV.b * 255)
			
			if data.Callback then
				data.Callback(HSV)
			end
		end
		
		local function updateHSV()
			H, S, V = color:rgbToHsv(HSV.r * 255, HSV.g * 255, HSV.b * 255)
		end
		
		local H_set = gui:sliderXY(guiObject.H, {guiObject.H}, function(X, Y, u)
			if not u then H = 1 - Y end
			guiObject.H.Locator.Position = UDim2.new(0.5, 0, Y, 0)
			newValue()
		end)
		
		local SV_set = gui:sliderXY(guiObject.SV, {guiObject.SV}, function(X, Y, u)
			if not u then S = X; V = 1 - Y; end
			guiObject.SV.Locator.Position = UDim2.new(X, 0, Y, 0)
			newValue()
		end)
		
		guiObject.R.FocusLost:Connect(function()
			HSV = Color3.new(guiObject.R.Text / 255, HSV.g, HSV.b)
			updateHSV()
			newValue()
		end)
		guiObject.G.FocusLost:Connect(function()
			HSV = Color3.new(HSV.r, guiObject.G.Text / 255, HSV.b)
			updateHSV()
			newValue()
		end)
		guiObject.B.FocusLost:Connect(function()
			HSV = Color3.new(HSV.r, HSV.g, guiObject.B.Text / 255)
			updateHSV()
			newValue()
		end)
		
		newValue()
		SV_set(S, 1 - V)
		H_set(0, H)
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextEnabled
		
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		return guiObject
	end
	
	function lib.Number(data, dataArray)
		local guiObject = Number:Clone()
		local Value = gui:unpack(saveData.Options[data.ID].Value, "number") or data.Default or math.floor(data.Min + (data.Max - data.Min) / 2)
		local guiData = {}
		
		local dMax = data.Max - data.Min
		local dValue = (Value - data.Min) / dMax
		
		data.Round = data.Round or 1
		
		local newValue = function(delta)
			local exactValue = data.Min + (data.Max - data.Min) * delta
			Value = math.floor(exactValue / data.Round) * data.Round
			Value = math.clamp(Value, data.Min, data.Max)
			guiObject.Indicator.Value.Text = tostring(Value)
			
			if data.Callback then
				data.Callback(Value)
			end
			saveData.Options[data.ID].Value = gui:pack(Value, "number")
		end
		
		local slideSet = gui:createSlider(guiObject.ValueFrame, {guiObject.Label, guiObject.Indicator}, newValue)
		slideSet(math.clamp(dValue, 0, 1))
		
		guiObject.Indicator.MouseButton1Down:Connect(newValue)
		guiObject.Label.MouseButton1Down:Connect(newValue)
		newValue(math.clamp(dValue, 0, 1))
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextEnabled
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		return guiObject
	end
	
	function lib.Execute(data, dataArray)
		local guiObject = Execute:Clone()
		local guiData = {}
		
		local newValue = function(val)
			if data.Callback then
				data.Callback()
			end
		end
		
		guiObject.MouseEnter:Connect(function()
			gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 40, 0, 25)})
		end)
		
		guiObject.MouseLeave:Connect(function()
			gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 0, 0, 25)})
		end)
		
		guiObject.Indicator.MouseButton1Down:Connect(newValue)
		guiObject.Label.MouseButton1Down:Connect(newValue)
		newValue(true)
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextEnabled
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		return guiObject
	end
	
	function lib.Mode(data, dataArray)
		local guiObject = Mode:Clone()
		local valueIndex = gui:unpack(saveData.Options[data.ID].Value, "number") or data.Default or 1
		local guiData = {}
		
		local newValue = function(val)
			if val == true then else
				valueIndex = (valueIndex % #data.Modes) + 1
			end
			
			local Value = data.Modes[valueIndex]
			gui:setText(guiObject.Mode, Value)
			
			if data.Callback then
				data.Callback(Value)
			end
			saveData.Options[data.ID].Value = gui:pack(valueIndex)
		end
		
		guiObject.Mode.MouseButton1Down:Connect(newValue)
		guiObject.Label.MouseButton1Down:Connect(newValue)
		newValue(true)
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextEnabled
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		return guiObject
	end
	
	function lib.Hotkey(data, dataArray)
		local guiObject = Mode:Clone()
		local hotkeyInput = gui:unpack(saveData.Hotkeys[data.ID], "string") or data.Hotkey or ""
		local guiData = {}
		
		local lastInput = hotkeyInput
		local mouseIn = false
		
		guiObject.Name = "Z"
		
		local newValue = function(val)
			local input
			gui:setText(guiObject.Mode, "...")
			saveData.Hotkeys[data.ID] = nil
			
			if not val then
				input = lastInput
				mouseIn = true
				
				lastInput = nil
				
				repeat wait() until mouseIn == false or lastInput
			end
			
			if not lastInput then
				lastInput = hotkeyInput
			end
			
			saveData.Hotkeys[data.ID] = tostring(lastInput)
			hotkeyFunctions[data.ID] = data.callback
			
			hotkeyInput = tostring(lastInput)
			saveData.Options[data.ID].Value = hotkeyInput
			gui:setText(guiObject.Mode, hotkeyInput:sub(14))
		end
		
		UserInputService.InputBegan:Connect(function(input)
			if input.KeyCode == Enum.KeyCode.Unknown then return end
			if input.KeyCode == Enum.KeyCode.Backspace then lastInput = "" return end
			lastInput = tostring(input.KeyCode)
		end)
		
		guiObject.Mode.MouseButton1Down:Connect(function() newValue() end)
		guiObject.Label.MouseButton1Down:Connect(function() newValue() end)
		guiObject.MouseLeave:Connect(function()
			mouseIn = false
		end)
		newValue(true)
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextEnabled
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, "Hotkey")
		gui:textColorOnHover(guiObject.Label, guiData)
		
		guiObject.Parent = dataArray.Object.OptionsFrame
		
		return guiObject
	end
	
	function lib.Toggle(data, dataArray)
		local guiObject = Toggle:Clone()
		local Value = gui:unpack(saveData.Options[data.ID].Value, "boolean") or data.Default or false
		local guiData = {}
		
		local modFrame = ModLabel:Clone()
		modFrame.Parent = Mods
		modFrame.TextColor3 = Colors[math.random(1, #Colors)]
		modFrame.Visible = false
		gui:setText(modFrame, data.Name)
		
		guiObject.Name = data.Name
		
		local newValue = function(val, set)
			if val == true then
			else
				if set then
					Value = set
				else
					Value = not Value
				end
			end
			
			if Value then
				gui.tween(guiObject.Indicator, "Sine", "Out", .25, {BackgroundColor3 = Color3.fromRGB(60, 222, 60)})
				guiObject.Indicator.Text = "ON"
				guiData.baseColor = colors.TextEnabled
			else
				gui.tween(guiObject.Indicator, "Sine", "Out", .25, {BackgroundColor3 = Color3.fromRGB(222, 60, 60)})
				guiObject.Indicator.Text = "OFF"
				guiData.baseColor = colors.TextDisabled
			end
			
			if data.Callback then
				data.Callback(Value)
			end
			
			saveData.Options[data.ID].Value = gui:pack(Value)
			modFrame.Visible = Value
			
		end
		
		guiObject.MouseEnter:Connect(function()
			gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 40, 0, 25)})
		end)
		
		guiObject.MouseLeave:Connect(function()
			gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 0, 0, 25)})
		end)
		
		gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 0, 0, 25)})
		guiObject.Indicator.MouseButton1Down:Connect(function() newValue() end)
		guiObject.Label.MouseButton1Down:Connect(function() newValue() end)
		newValue(true)
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextDisabled
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		data.callback = newValue
		
		return guiObject
	end
	
	function lib.Checkbox(data, dataArray)
		local guiObject = Checkbox:Clone()
		local Value = gui:unpack(saveData.Options[data.ID].Value, "boolean") or data.Default or false
		local guiData = {}
		
		guiObject.Name = "0"
		
		local newValue = function(val)
			if val == true then else
				Value = not Value
			end
			if Value then
				gui.tween(guiObject.Indicator, "Sine", "Out", .35, {Size = UDim2.new(0, 35, 0, 35)})
				guiData.baseColor = colors.TextEnabled
			else
				gui.tween(guiObject.Indicator, "Sine", "Out", .35, {Size = UDim2.new(0, 0, 0, 35)})
				guiData.baseColor = colors.TextDisabled
			end
			if data.Callback then
				data.Callback(Value)
			end
			saveData.Options[data.ID].Value = gui:pack(Value)
		end
		
		guiObject.Indicator.MouseButton1Down:Connect(newValue)
		guiObject.Label.MouseButton1Down:Connect(newValue)
		newValue(true)
		
		guiData.ySize = 0
		guiData.Open = false
		guiData.baseColor = colors.TextDisabled
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		return guiObject
	end
	
	function lib.Frame(data, dataArray)
		local guiObject = Frame:Clone()
		
		local guiData = {}
		guiData.ySize = 0
		guiData.Open = false
		
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Label, data.Name)
		gui:textColorOnHover(guiObject.Label, guiData)
		
		return guiObject
	end
	
	function lib.Container(data, dataArray)
		local guiObject = Container:Clone()
		
		guiObject.Position = gui:unpack(saveData.Options[data.ID].Position, "UDim2") or UDim2.new(0, 3, 0, 3 + gui:getn(settingsArray[2]) * 38)
		
		local guiData = {}
		guiData.yPos = 0
		guiData.ySize = 0
		guiData.Open = false
		
		gui:textColorOnHover(guiObject.Title, guiData)
		gui:createList(guiObject, guiData)
		gui:setText(guiObject.Title, data.Name)
		gui:makeDraggable(guiObject, function(x, y)
			guiData.yPos = y
			saveData.Options[data.ID].Position = gui:pack(guiObject.Position)
		end)
		
		return guiObject
	end
	
	-- UI Creation Library
	function gui.create(self, guiType, data)
		if self == gui then
			self = settingsArray
		end
		
		data.ID = data.Name .. "_" .. (self[1].Name or "TOP")
		
		if not saveData.Options[data.ID] then
			saveData.Options[data.ID] = {}
		end
		
		if self[1].Object:FindFirstChild("Dropdown") then
			self[1].Object.Dropdown.Visible = true
		end
		
		local dataArray = {}
		local objectArray = {}
		local selfArray = {dataArray, objectArray, create = gui.create, callback = data.Callback}
		dataArray.Name = data.Name
		dataArray.Data = data
		dataArray.Object = lib[guiType](data, dataArray)
		dataArray.self = selfArray
		
		if guiType == "Toggle" then
			lib.Hotkey(data, dataArray)
		end
		if data.Hint then
			local Object = dataArray.Object
			gui:addHint(Object:FindFirstChild("Title") or Object:FindFirstChild("Label"), data.Hint)
		end
		
		self[1][data.Name] = selfArray
		self[2][data.Name] = dataArray.Object
		
		dataArray.Object.Parent = self[1].Object:FindFirstChild("OptionsFrame") or self[1].Object
		
		return dataArray
	end
	
	-- Connection Stuff
	game:GetService("RunService").RenderStepped:Connect(function()
		for _, func in pairs(connections) do
			func()
		end
	end)
	
	UserInputService.InputBegan:Connect(function(input, gameProcessed)
		if gameProcessed then return end
		for id, key in pairs(saveData.Hotkeys) do
			if key == tostring(input.KeyCode) then
				hotkeyFunctions[id]()
			end
		end
	end)
	
	Mods.Text = "Cardinality " .. _V
	
	game.Close:Connect(function()
		Save()
	end)
	
	return {gui, saveData, screenGui}
end)()

--// Variables
local gui = GUIData[1]
local screenGui = GUIData[3]

local screenscale = 250
local opacity = 1

return gui, screenGui, screenscale, opacity
