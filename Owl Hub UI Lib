local OwlLib = {Content = {}};
local config = {};

local placeID = tostring(game.PlaceId);
local httpService = game:GetService("HttpService");

pcall(function()
    config = httpService:JSONDecode(readfile(placeID .. ".txt"));
end);

local function saveConfig()
    writefile(placeID .. ".txt", httpService:JSONEncode(config));
end;

local oldScript = script;
local popupGui = game:GetObjects("rbxassetid://4743303040")[1];
popupGui.Parent = game:GetService("CoreGui");
popupGui.Name = httpService:GenerateGUID(false);
script = popupGui.mainScript;
local popup = loadstring(popupGui.mainScript.Source)();
script = oldScript;

local owlLibGui = game:GetObjects("rbxassetid://4530443679")[1];
owlLibGui.Parent = game:GetService("CoreGui");
owlLibGui.Name = httpService:GenerateGUID(false);
local mainFrame = owlLibGui.mainFrame;

local tweenService = game:GetService("TweenService");
local inputService = game:GetService("UserInputService");

local firstBodyFrame;
local startPos;
local dragging = false;
local draggableInput;
local draggableStart;

local mouse = game:GetService("Players").LocalPlayer:GetMouse();
local clamp = math.clamp;
local floor = math.floor;
local fromHSV = Color3.fromHSV;
local fromRGB = Color3.fromRGB;
local newUDim2 = UDim2.new;

mainFrame.topBarFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true;
        draggableStart = input.Position;
        startPos = mainFrame.AbsolutePosition;
    end;
end);

mainFrame.topBarFrame.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false;
    end;
end);

inputService.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement and dragging then
        mainFrame.Position = newUDim2(0, startPos.X + (input.Position.X - draggableStart.X), 0, startPos.Y + (input.Position.Y - draggableStart.Y));
    end;
end);

local exitTween = tweenService:Create(mainFrame.topBarFrame.exitBtn, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageTransparency = 0});
local exitTween1 = tweenService:Create(mainFrame.topBarFrame.exitBtn, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageTransparency = 0.2});
local miniTween = tweenService:Create(mainFrame.topBarFrame.miniBtn, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageTransparency = 0});
local miniTween2 = tweenService:Create(mainFrame.topBarFrame.miniBtn, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageTransparency = 0.2});

mainFrame.topBarFrame.exitBtn.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        exitTween:Play();
    end;
end);

mainFrame.topBarFrame.exitBtn.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        exitTween1:Play();
    end;
end);

mainFrame.topBarFrame.exitBtn.MouseButton1Click:Connect(function()
    mainFrame:TweenSize(newUDim2(0, 387, 0, 27), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.25);
    wait(0.25);
    mainFrame.topBarFrame:TweenSize(newUDim2(0, 0, 0, 27), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.25);
    mainFrame:TweenSize(newUDim2(0, 0, 0, 27), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.25);
    wait(0.25);
    owlLibGui:Destroy();
end);

mainFrame.topBarFrame.miniBtn.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        miniTween:Play();
    end;
end);

mainFrame.topBarFrame.miniBtn.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        miniTween2:Play();
    end;
end);

mainFrame.topBarFrame.miniBtn.MouseButton1Click:Connect(function()
    if mainFrame.Size ~= newUDim2(0, 387, 0, 27) then
        mainFrame:TweenSize(newUDim2(0, 387, 0, 27), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.25, true);
    else
        mainFrame:TweenSize(newUDim2(0, 387, 0, 225), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.25, true);
    end;
end);

inputService.InputBegan:Connect(function(input, onGui)
    if not onGui and (input.KeyCode == Enum.KeyCode.P or input.KeyCode == Enum.KeyCode.RightShift) then
        owlLibGui.Enabled = not owlLibGui.Enabled;
    end;
end);

function OwlLib:SetCategory() end;

function OwlLib.Content:Resize(scrollingFrame)
    scrollingFrame.CanvasSize = newUDim2(0, 0, 0, (#scrollingFrame:GetChildren() - 1) * 36);
end;

function OwlLib.Content:Ripple(btn)
    spawn(function()
		local rippleEffect = Instance.new("ImageLabel", btn);
		local rippleEffectInner = Instance.new("ImageLabel", rippleEffect);
		rippleEffect.Name = "rippleEffect";
		rippleEffect.BackgroundTransparency = 1;
		rippleEffect.BorderSizePixel = 0;
		rippleEffect.Image = "rbxassetid://2708891598";
		rippleEffect.ImageColor3 = fromRGB(244, 244, 244);
		rippleEffect.ImageTransparency = 0.7;
		rippleEffect.ScaleType = Enum.ScaleType.Fit;
		rippleEffectInner.Name = "rippleEffect";
		rippleEffectInner.AnchorPoint = Vector2.new(0.5, 0.5);
		rippleEffectInner.BackgroundTransparency = 1;
		rippleEffectInner.BorderSizePixel = 0;
		rippleEffectInner.Position = newUDim2(0.5, 0, 0.5, 0);
		rippleEffectInner.Size = newUDim2(0.93, 0, 0.93, 0);
		rippleEffectInner.Image = "rbxassetid://2708891598";
		rippleEffectInner.ImageColor3 = fromRGB(45, 45, 45);
		rippleEffectInner.ImageTransparency = 0.7;
		rippleEffectInner.ScaleType = Enum.ScaleType.Fit;
		rippleEffect.Position = newUDim2(0, mouse.X - rippleEffect.AbsolutePosition.X, 0, mouse.Y - rippleEffect.AbsolutePosition.Y);
		rippleEffect:TweenSizeAndPosition(newUDim2(10, 0, 10, 0), newUDim2(-4.5, 0, -4.5, 0), "Out", "Quad", 0.33);
		for i = 1, 10 do
			rippleEffect.ImageTransparency = rippleEffect.ImageTransparency + 0.01;
			wait();
		end;
		rippleEffect:Destroy();
	end)
end;

function OwlLib.Content:initBtnEffect(btn)
	local btnHover = tweenService:Create(btn, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 0.85});
	local btnHover1 = tweenService:Create(btn, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 1});

    btn.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            btnHover:Play();
        end;
    end);

    btn.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            btnHover1:Play();
        end;
    end);
end;

function OwlLib:new(title)
    local self = setmetatable({}, {__index = self.Content});

    self.bodyFrame = game:GetObjects("rbxassetid://4531111462")[1];
    self.bodyFrame.Parent = mainFrame;
    self.bodyFrame.Name = title .. "BodyFrame";
    self.bodyFrame.Visible = false;
	
	local tabBtn = game:GetObjects("rbxassetid://4530456835")[1];
    tabBtn.Parent = mainFrame.tabsFrame;
    tabBtn.tabLabel.Text = title;
    tabBtn.Size = newUDim2(0, tabBtn.tabLabel.TextBounds.X + 20, 1, 0, 0);

    if not firstBodyFrame then
        firstBodyFrame = self.bodyFrame;
        self.bodyFrame.Visible = true;
		tabBtn.ImageColor3 = fromRGB(30, 30, 30);
    end;

    --[[tabBtn.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement and tabBtn.ImageColor3 ~= fromRGB(50, 50, 50) then
            tweenService:Create(tabBtn, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageColor3 = fromRGB(40, 40, 40)}):Play();
        end;
    end);

    tabBtn.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement and tabBtn.ImageColor3 ~= fromRGB(50, 50, 50) then
            tweenService:Create(tabBtn, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageColor3 = fromRGB(30, 30, 30)}):Play();
        end;
    end);]]

    tabBtn.MouseButton1Click:Connect(function()
        for i, v in next, mainFrame:GetChildren() do
            if v.Name:find("BodyFrame") then
                if v ~= self.bodyFrame then
                    v.Visible = false;
                end;
            end;
        end;
        for i, v in next, mainFrame.tabsFrame:GetChildren() do
            if v:IsA("ImageButton") then
                v.ImageColor3 = fromRGB(50, 50, 50);
            end;
        end;
        tabBtn.ImageColor3 = fromRGB(30, 30, 30);
        self.bodyFrame.Visible = true;
    end);

    return self;
end;

function OwlLib.Content:newBtn(title, callback, noToggle)
    self:Resize(self.bodyFrame);

    if not noToggle then
        local enabled = config[title] and true or false;
        if enabled then
            callback(enabled);
            popup:new("Enabled " .. title);
        end;
        
        local btn = game:GetObjects("rbxassetid://4531129509")[1];
        btn.Parent = self.bodyFrame;
        btn.titleLabel.Text = title;
        btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
        btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 50, 0, 30);

        self:initBtnEffect(btn);

        local toggle = {
            [true] = fromRGB(0, 194, 94),
            [false] = fromRGB(180, 0, 0)
        };

        tweenService:Create(btn.statusFrame, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = toggle[enabled]}):Play();

        btn.MouseButton1Click:Connect(function()
            self:Ripple(btn);
            enabled = not enabled;
            config[title] = enabled;
            saveConfig();
            tweenService:Create(btn.statusFrame, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = toggle[enabled]}):Play();
            callback(enabled);
            popup:new((enabled and "Enabled " or "Disabled ") .. title);
        end);

        return {
            Set = function(self, bool) 
                enabled = bool;
                if not noToggle then
                    config[title] = enabled;
                    saveConfig();
                    tweenService:Create(btn.statusFrame, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = toggle[enabled]}):Play();
                    callback(enabled);
                    popup:new((enabled and "Enabled " or "Disabled ") .. title);
                end;
            end;
        };
    elseif noToggle then
        local btn = game:GetObjects("rbxassetid://4531209476")[1];
        btn.Parent = self.bodyFrame;
        btn.titleLabel.Text = title;
        btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
        btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 17, 0, 30);

        self:initBtnEffect(btn);

        btn.MouseButton1Click:Connect(function()
            self:Ripple(btn);
            callback();
            popup:new("Enabled " .. title);
        end);

        return {
            Fire = function(self) 
                callback();
                popup:new("Enabled " .. title);
            end;
        };
    end;
end;

function OwlLib.Content:newSlider(title, callback, min, max, startPoint)
    self:Resize(self.bodyFrame);

    local dragging = false;
    
    local sliderFrame = game:GetObjects("rbxassetid://4531326550")[1];
    sliderFrame.Parent = self.bodyFrame;
    sliderFrame.titleLabel.Text = title;
    sliderFrame.titleLabel.Size = newUDim2(0, sliderFrame.titleLabel.TextBounds.X, 1, 0);
    sliderFrame.Size = newUDim2(0, sliderFrame.titleLabel.Size.X.Offset + 195, 0, 30);

    local startPoint = config[title] and tonumber(config[title]) or startPoint;

    local sliderIndicatorFrame = sliderFrame.sliderIndicatorFrame;
    sliderIndicatorFrame.valueLabel.Text = tostring(startPoint and floor((startPoint / max) * (max - min) + min) or 0);

    local slidingFrame = sliderFrame.sliderIndicatorFrame.slidingFrame;
    slidingFrame.Size = newUDim2((startPoint or 0) / max, 0, 1, 0);

    if startPoint then
        local callbackValue = floor((startPoint / max) * (max - min) + min);
        callback(callbackValue);
        if config[title] then
            popup:new("Set " .. title .. " to " .. tostring(callbackValue));
        end;
    end;

    local function slide(input)
        local pos = newUDim2(clamp((input.Position.X - sliderIndicatorFrame.AbsolutePosition.X) / sliderIndicatorFrame.AbsoluteSize.X, 0, 1), 0, 1, 0);
        slidingFrame:TweenSize(pos, Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.2, true);
        local value = floor(((pos.X.Scale * max) / max) * (max - min) + min);
        sliderIndicatorFrame.valueLabel.Text = tostring(value);
        callback(value);
    end;

    sliderIndicatorFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            slide(input);
			dragging = true;
		end;
	end);
	
	sliderIndicatorFrame.InputEnded:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = false;
            config[title] = sliderIndicatorFrame.valueLabel.Text;
            saveConfig();
            popup:new("Set " .. title .. " to " .. sliderIndicatorFrame.valueLabel.Text);
		end;
    end);

	inputService.InputChanged:Connect(function(input)
		if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
			slide(input);
		end;
	end);
end;

function OwlLib.Content:newTextbox(title, callback, presetText, noCallbackOnStart)
    self:Resize(self.bodyFrame);

    local btn = game:GetObjects("rbxassetid://4531463561")[1];
    btn.Parent = self.bodyFrame;
    btn.titleLabel.Text = title;
    btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
    btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 100, 0, 30);

    local presetText = (config[title] and config[title]) or (presetText and presetText or "");
    if config[title] then
        popup:new("Set " .. title .. " to " .. config[title]);
    end;

    btn.inputBox.Text = presetText;

    if not noCallbackOnStart then
        callback(presetText);
    end;

    btn.inputBox.FocusLost:Connect(function()
        config[title] = btn.inputBox.Text;
        saveConfig();
        callback(btn.inputBox.Text);
        popup:new("Set " .. title .. " to " .. btn.inputBox.Text);
    end);
end;

function OwlLib.Content:newBind(title, callback, presetKeyCode)
    self:Resize(self.bodyFrame);

    local enabled = false;
    local listening = false;
    local presetKeyCode = config[title] and Enum.KeyCode[config[title]] or presetKeyCode;
    local activated = presetKeyCode and true or false;
    local keyCode = presetKeyCode;

    local btn = game:GetObjects("rbxassetid://4531229816")[1];
    btn.Parent = self.bodyFrame;
    btn.titleLabel.Text = title;
    btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
    btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 90, 0, 30);

    btn.bindBtn.Text = presetKeyCode and string.upper(tostring(string.char(presetKeyCode.Value))) or "KEY";
    if config[title] then
        popup:new("Set " .. title .. " to " .. string.upper(tostring(string.char(presetKeyCode.Value))));
    end;

    inputService.InputBegan:Connect(function(input, onGui)
        if onGui then return; end;

        if listening and not activated then
            pcall(function()
                btn.bindBtn.Text = string.upper(tostring(string.char(input.KeyCode.Value)));
                listening = false;
                config[title] = input.KeyCode.Name;
                saveConfig();
                keyCode = input.KeyCode;
                activated = true;
                popup:new("Set " .. title .. " to " .. string.upper(tostring(string.char(input.KeyCode.Value))));
            end);
		elseif activated and not listening and input.KeyCode == keyCode then
            enabled = not enabled;
            
            callback(enabled);
        end;
    end);

    btn.bindBtn.MouseButton1Click:Connect(function()
        btn.bindBtn.Text = "...";

        activated = false;
        listening = true;
    end);
end;

function OwlLib.Content:newCBind(title, callback, presetKeyCode)
    self:Resize(self.bodyFrame);

    local enabled = false;
    local presetKeyCode = presetKeyCode and presetKeyCode;
    local shortNames = {
        RightControl = 'RightCtrl';
        LeftControl = 'LeftCtrl';
        LeftShift = 'LShift';
        RightShift = 'RShift';
        MouseButton1 = "Mouse1";
        MouseButton2 = "Mouse2";
    };
    if config[title] then
        local keyboard = config[title]:find("Keyboard");
        if keyboard then
            presetKeyCode = Enum.KeyCode[config[title]:gsub("Keyboard", "")];
        else
            presetKeyCode = Enum.UserInputType[config[title]];
        end;
        popup:new("Set " .. title .. " to " .. (shortNames[presetKeyCode.Name] or presetKeyCode.Name));
    end;
    local activated = presetKeyCode and true or false;
    local banned = {
        Return = true;
        Space = true;
        Tab = true;
        Unknown = true;
    }
    
    local function isreallypressed(bind, inp)
        local key = bind
        if typeof(key) == "Instance" then
            if key.UserInputType == Enum.UserInputType.Keyboard and inp.KeyCode == key.KeyCode then
                return true;
            elseif tostring(key.UserInputType):find("MouseButton") and inp.UserInputType == key.UserInputType then
                return true
			end
        end
        if tostring(key):find'MouseButton' then
            return key == inp.UserInputType
        else
            return key == inp.KeyCode
        end
    end
    
    local allowed = {
        MouseButton1 = true;
        MouseButton2 = true;
    };

    local nm = (presetKeyCode and (shortNames[presetKeyCode.Name] or presetKeyCode.Name) or "None");
    local keyCode = presetKeyCode;

    local btn = game:GetObjects("rbxassetid://4531229816")[1];
    btn.Parent = self.bodyFrame;
    btn.titleLabel.Text = title;
    btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
    btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 90, 0, 30);

    btn.bindBtn.Text = nm;

    inputService.InputBegan:Connect(function(input, onGui)
        if onGui then return; end;
        if activated and isreallypressed(keyCode, input) then
            callback(true);
        end;
    end);
    inputService.InputEnded:Connect(function(input, onGui)
        if onGui then return; end;
        if activated and not listening and isreallypressed(keyCode, input) then
            callback(false);
        end;
    end);    
    btn.bindBtn.MouseButton1Click:Connect(function()
        btn.bindBtn.Text = "...";
        activated = false;
        local input, onGui = inputService.InputBegan:Wait();
        config[title] = (input.UserInputType ~= Enum.UserInputType.Keyboard and input.UserInputType.Name or input.KeyCode.Name .. "Keyboard");
        saveConfig();
        keyCode = input;
        local name = (input.UserInputType ~= Enum.UserInputType.Keyboard and (shortNames[input.UserInputType.Name] or input.UserInputType.Name) or input.KeyCode.Name);
        btn.bindBtn.Text = name
        activated = true;
        popup:new("Set " .. title .. " to " .. (shortNames[input.UserInputType.Name] or input.UserInputType.Name));
    end);
end;

function OwlLib.Content:newColorPicker(title, callback, presetColor)
    self:Resize(self.bodyFrame);

    local oldSize;
    local rainbow = false;
    local hueSatDragging = false;
    local valueDragging = false;

    local btn = game:GetObjects("rbxassetid://4531551348")[1];
    btn.Parent = self.bodyFrame;
    btn.titleLabel.Text = title;
    btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
    btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 50, 0, 30);

    local colorFrame = btn.colorFrame;
    local colorPickingFrame = btn.colorPickingFrame;
    local rainbowBtn = colorPickingFrame.rainbowBtn;
    local hueSatFrame = colorPickingFrame.hueSatFrame;
    local valueFrame = colorPickingFrame.valueFrame;
    local hueSatIndicatorFrame = hueSatFrame.hueSatIndicatorFrame;
    local valueIndicatorFrame = valueFrame.valueIndicatorFrame;

    local presetColor = presetColor and presetColor or fromRGB(255, 255, 255);
    if config[title] then
        if config[title]["R"] then
            presetColor = fromRGB(config[title]["R"], config[title]["G"], config[title]["B"]);
            popup:new("Set " .. title .. " to " .. floor(config[title]["R"] * 255) .. " " .. floor(config[title]["G"] * 255) .. " " .. floor(config[title]["B"] * 255));
        elseif config[title] == "Rainbow" then
            rainbow = true;
            popup:new("Set " .. title .. " to rainbow");
        end;
    end;

    callback(presetColor);

    colorFrame.BackgroundColor3 = presetColor;

    self:initBtnEffect(btn);

    btn.MouseButton1Click:Connect(function()
        if not colorPickingFrame.Visible then
            oldSize = self.bodyFrame.CanvasSize;
            self.bodyFrame.CanvasSize = oldSize + newUDim2(0, 0, 0, 170);
            colorPickingFrame.Visible = true;
            colorPickingFrame:TweenSize(newUDim2(0, 170, 0, 120), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.2, true);
        elseif colorPickingFrame.Visible then
            colorPickingFrame:TweenSize(newUDim2(0, 170, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.2, true);
            wait(0.15);
            colorPickingFrame.Visible = false;
            self.bodyFrame.CanvasSize = oldSize;
        end;
    end);

    rainbowBtn.MouseButton1Click:Connect(function()
        config[title] = "Rainbow";
        saveConfig();
        rainbow = true;
        popup:new("Set " .. title .. " to rainbow");
    end);
    
    hueSatFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            hueSatDragging = true;
        end;
    end);
    
    hueSatFrame.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            hueSatDragging = false;
            config[title] = {R = colorFrame.BackgroundColor3.R * 255, G = colorFrame.BackgroundColor3.G * 255, B = colorFrame.BackgroundColor3.B * 255};
            saveConfig();
            popup:new("Set " .. title .. " to " .. floor(colorFrame.BackgroundColor3.R * 255) .. " " .. floor(colorFrame.BackgroundColor3.G * 255) .. " " .. floor(colorFrame.BackgroundColor3.B * 255));
        end;
    end);

    valueFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            valueDragging = true;
        end;
    end)
    
    valueFrame.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            valueDragging = false;
            config[title] = {R = colorFrame.BackgroundColor3.R * 255, G = colorFrame.BackgroundColor3.G * 255, B = colorFrame.BackgroundColor3.B * 255};
            saveConfig();
            popup:new("Set " .. title .. " to " .. floor(colorFrame.BackgroundColor3.R) .. " " .. floor(colorFrame.BackgroundColor3.G) .. " " .. floor(colorFrame.BackgroundColor3.B));
        end;
    end);

    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if hueSatDragging and input.UserInputType == Enum.UserInputType.MouseMovement then
            rainbow = false;
            hueSatIndicatorFrame.Position = newUDim2(clamp((input.Position.X - hueSatFrame.AbsolutePosition.X) / hueSatFrame.AbsoluteSize.X, 0, 1), 0, clamp((input.Position.Y - hueSatFrame.AbsolutePosition.Y) / hueSatFrame.AbsoluteSize.Y, 0, 1), 0);
            valueIndicatorFrame.BackgroundColor3 = fromHSV(h, 1 - (1 - hueSatIndicatorFrame.Position.Y.Scale), 1);
            colorFrame.BackgroundColor3 = fromHSV(hueSatIndicatorFrame.Position.X.Scale, 1 - hueSatIndicatorFrame.Position.Y.Scale, 1 - valueIndicatorFrame.Position.Y.Scale);
            valueFrame.ImageColor3 = fromHSV(hueSatIndicatorFrame.Position.X.Scale, 1 - hueSatIndicatorFrame.Position.Y.Scale, 1);
            callback(colorFrame.BackgroundColor3);
        elseif valueDragging and input.UserInputType == Enum.UserInputType.MouseMovement then
            rainbow = false;
            valueIndicatorFrame.Position = newUDim2(0, 0, clamp((input.Position.Y - valueFrame.AbsolutePosition.Y) / valueFrame.AbsoluteSize.Y, 0, 1), 0);
            valueIndicatorFrame.BackgroundColor3 = fromHSV(h, 1 - (1 - hueSatIndicatorFrame.Position.Y.Scale), 1);
            colorFrame.BackgroundColor3 = fromHSV(hueSatIndicatorFrame.Position.X.Scale, 1 - hueSatIndicatorFrame.Position.Y.Scale, 1 - valueIndicatorFrame.Position.Y.Scale);
            valueFrame.ImageColor3 = fromHSV(hueSatIndicatorFrame.Position.X.Scale, 1 - hueSatIndicatorFrame.Position.Y.Scale, 1);
            callback(colorFrame.BackgroundColor3);
        end;
    end);

    spawn(function()
        while true do
            for i = 1, 230 do
                rainbowBtn.TextColor3 = fromHSV(i / 230, 1, 1);
                if rainbow then
                    colorFrame.BackgroundColor3 = fromHSV(i / 230, 1, 1);
                    callback(fromHSV(i / 230, 1, 1));
                end;
                wait();
            end;
            wait();
        end;
    end);
end;

function OwlLib.Content:newDropdown(title, callback, list, noCallbackOnStart)
    self:Resize(self.bodyFrame);

    local oldSize;
    local btn = game:GetObjects("rbxassetid://4531687341")[1];
    btn.Parent = self.bodyFrame;
    btn.titleLabel.Text = title;
    btn.titleLabel.Size = newUDim2(0, btn.titleLabel.TextBounds.X, 1, 0);
    btn.Size = newUDim2(0, btn.titleLabel.Size.X.Offset + 80, 0, 30);

    if not noCallbackOnStart then
        callback(config[title] and config[title] or list[1]);
        if config[title] then
            popup:new("Set " .. title .. " to " .. config[title]);
        end;
    end;

    local arrowLabel = btn.arrowLabel;
    local bodyFrame = btn.bodyFrame;

    self:initBtnEffect(btn);
    
    local function refresh(list)
        for i, v in next, bodyFrame:GetChildren() do
            if not v:IsA("UIListLayout") then v:Destroy(); end;
        end
        for i, v in next, list do
            local btn = game:GetObjects("rbxassetid://4531683854")[1];
            btn.Parent = bodyFrame;
            btn.Text = v;
            btn.ZIndex = 2;

            local btnHover = tweenService:Create(btn, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 0.5});
            local btnHover1 = tweenService:Create(btn, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 1});

            btn.InputBegan:Connect(function(input)
                if input.UserInputType == Enum.UserInputType.MouseMovement then
                    btnHover:Play();
                end;
            end);

            btn.InputEnded:Connect(function(input)
                if input.UserInputType == Enum.UserInputType.MouseMovement then
                    btnHover1:Play();
                end;
			end);

            local arrowTween = tweenService:Create(arrowLabel, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = 180});

            btn.MouseButton1Click:Connect(function()
                config[title] = v;
                saveConfig();
                callback(v);
                popup:new("Set " .. title .. " to " .. v);
                arrowTween:Play();
                bodyFrame:TweenSize(newUDim2(0, 170, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.2, true);
                wait(0.15);
                bodyFrame.Visible = false;
                self.bodyFrame.CanvasSize = oldSize;
            end);
        end;
    end

    refresh(list);

    local arrowTween = tweenService:Create(arrowLabel, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = 0});
    local arrowTween1 = tweenService:Create(arrowLabel, TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Rotation = 180});

    btn.MouseButton1Click:Connect(function()
        if not bodyFrame.Visible then
            oldSize = self.bodyFrame.CanvasSize;
            self.bodyFrame.CanvasSize = oldSize + newUDim2(0, 0, 0, 170);
            bodyFrame.Visible = true;
            arrowTween:Play();
            bodyFrame:TweenSize(newUDim2(0, 170, 0, (#bodyFrame:GetChildren() - 1) * 27), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.2, true);
        elseif bodyFrame.Visible then
            arrowTween1:Play();
            bodyFrame:TweenSize(newUDim2(0, 170, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.2, true);
            wait(0.15);
            bodyFrame.Visible = false;
            self.bodyFrame.CanvasSize = oldSize;
        end;
    end);

    return {
        Refresh = function(self, list)
            refresh(list);
        end
    }
end;

return OwlLib;
