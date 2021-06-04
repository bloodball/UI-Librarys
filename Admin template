local function instance(className,properties,children,funcs)
    local object = Instance.new(className,parent)

    for i, v in pairs(properties or {}) do
        object[i] = v
    end

    for i, self in pairs(children or {}) do
        self.Parent = object
    end

    for i, func in pairs(funcs or {}) do
        func(object)
    end

    return object
end
local function ts(object,tweenInfo,properties)
    if tweenInfo[2] and typeof(tweenInfo[2]) == 'string' then
        tweenInfo[2] = Enum.EasingStyle[ tweenInfo[2] ]
    end

    game:service('TweenService'):create(object, TweenInfo.new(unpack(tweenInfo)), properties):Play()
end
local function clone(self,newProperties,children)
    local clone = self:Clone()

    for property,value in next, (newProperties or {}) do
        clone[property] = value
    end

    for _,module in next, (children or {}) do
        module.Parent = clone
    end

    return clone
end
local function udim2(x1,x2,y1,y2)
    local t = tonumber
    return UDim2.new(t(x1),t(x2),t(y1),t(y2))
end
local function rgb(r,g,b)
    return Color3.fromRGB(r,g,b)
end
local function round(exact, quantum)
    local quant, frac = math.modf(exact/quantum)
    return quantum * (quant + (frac > 0.5 and 1 or 0))
end
local function border(self,borderSize,additional)
    borderSize = math.floor(borderSize / 2) == borderSize / 2 and borderSize or borderSize + 1

    local border = clone(self,{
        Parent = self,
        Position = udim2(0,borderSize/2,0,borderSize/2),
        Size = udim2(1,-borderSize,1,-borderSize)
    })

    if border:FindFirstChild('UICorner') then
        self.UICorner:GetPropertyChangedSignal('CornerRadius'):connect(function()
            border.UICorner.CornerRadius = UDim.new(self.UICorner.CornerRadius.Scale, self.UICorner.CornerRadius.Offset - 1)
        end)

        border.UICorner.CornerRadius = UDim.new(self.UICorner.CornerRadius.Scale, self.UICorner.CornerRadius.Offset - 1)
    end

    for property,value in next, (additional or {}) do
        border[property] = value
    end

    return border
end
local function scale(unscaled, minAllowed, maxAllowed, min, max)
	return (maxAllowed - minAllowed) * (unscaled - min) / (max - min) + minAllowed
end
local function service(v)
    return game:GetService(v);
end
local function half(x, y)
    return udim2(0.5, -(x / 2), 0.5, -(y / 2));
end

local admin = {
    Themes = {
        Dark = {
            BodyColor = rgb(30, 30, 30),
            TextFieldFrame = rgb(70, 70, 70),
            TextColor = rgb(255, 255, 255),
            PlaceholderTextColor = rgb(150, 150, 150),
            CommandListBackground = rgb(50, 50, 50),
            ScrollBarColor = rgb(255, 255, 255),
        },
        Light = {
            BodyColor = rgb(204, 199, 255),
            TextFieldFrame = rgb(129, 125, 191),
            TextColor = rgb(77, 67, 88),
            PlaceholderTextColor = rgb(175, 164, 255),
            CommandListBackground = rgb(109, 105, 171),
            ScrollBarColor = rgb(59, 55, 121),
        }
    }
}
local dragger = loadstring(game:HttpGet('https://raw.githubusercontent.com/boop71/cappuccino/main/v3/dragger.lua'))();
admin.New = function(data)
    if typeof(data) ~= 'table' then
        data = {}
    end
    local title = (typeof(data.Title) == 'string') and data.Title or 'Admin commands';
    pcall(function()
        service('CoreGui')[title]:Destroy()
    end)
    if typeof(data.Theme) ~= 'string' then
        data.Theme = 'Dark'
    end
    local commands = typeof(data.Commands) == 'table' and data.Commands or {
        ['nil commands'] = {
            Description = 'commands is either not a table or does not exist'
        }
    }
    local mouse = service('Players').LocalPlayer:GetMouse()
    local theme = admin.Themes[data.Theme]
    local sgui = instance('ScreenGui', {
        Parent = service('CoreGui'),
        Name = title
    });



    local mainFrame = instance('Frame', {
        Size = udim2(0, 200, 0, 30),
        Position = half(200, 30),
        Parent = sgui,
        BackgroundColor3 = theme.BodyColor,
        ClipsDescendants = true
    }, {
        instance('UICorner', {
            CornerRadius = UDim.new(0, 4)
        }),
        instance('Frame', {
            Name = 'TextFieldFrame',
            Size = udim2(0, 192, 0, 22),
            Position = udim2(0, 4, 0, 4),
            BackgroundColor3 = theme.TextFieldFrame
        }, {
            instance('UICorner', {
                CornerRadius = UDim.new(0, 4)
            }),
            instance('TextBox', {
                Text = '',
                PlaceholderText = 'Press , or click here to type',
                TextColor3 = theme.TextColor,
                PlaceholderColor3 = theme.PlaceholderTextColor,
                Size = udim2(1, -8, 1, 0),
                Position = udim2(0, 4, 0, 0),
                TextSize = 14,
                Font = 'Gotham',
                BackgroundTransparency = 1,
                Name = 'TextField',
                ClipsDescendants = true,
                TextXAlignment = 'Left',
            }),
        }),
        instance('TextLabel', {
            Text = title:sub(1, 20),
            BackgroundTransparency = 1,
            Font = 'GothamSemibold',
            TextSize = 16,
            Size = udim2(1, 0, 0, 32),
            TextTransparency = 1,
            Name = 'Title',
            TextColor3 = theme.TextColor
        }),
        instance('Frame', {
            Name = 'CommandListFrame',
            Size = udim2(1, -12, 1, -74),
            Position = udim2(0, 6, 0, 68),
            BackgroundColor3 = theme.CommandListBackground,
            BackgroundTransparency = 1,
        }, {
            instance('UICorner', {
                CornerRadius = UDim.new(0, 4)
            }),
            instance('ScrollingFrame', {
                Name = 'Commands', 
                BackgroundTransparency = 1,
                BorderSizePixel = 0,
                ScrollBarThickness = 5,
                ScrollBarImageTransparency = 1,
                ScrollBarImageColor3 = theme.ScrollBarColor,
                Size = udim2(1, -12, 1, -12),
                Position = udim2(0, 6, 0, 6)
            }, {
                instance('UIListLayout', {})
            }, {
                function(self)
                    self:GetPropertyChangedSignal('CanvasPosition'):connect(function()
                        ts(self, {0.3, 'Exponential'}, {
                            ScrollBarImageTransparency = 0.5
                        })
                    end)
                    spawn(function()
                        while true do
                            wait(1)
                            ts(self, {0.8, 'Sine'}, {
                                ScrollBarImageTransparency = 1
                            })
                        end
                    end)
                end
            })
        })
    });
    dragger.new(mainFrame);

    local state, cooldown = false, false
    spawn(function()
        while true do
            wait(0.5)
            cooldown = false
        end
    end)
    local function open()
        if not cooldown then
            state = true
            cooldown = true
            ts(mainFrame, {0.3, 'Exponential'}, {
                Size = udim2(0, 250, 0, 300),
                Position = udim2(0, mainFrame.AbsolutePosition.X - 20, 0, mainFrame.AbsolutePosition.Y - 30)
            })
            ts(mainFrame.TextFieldFrame, {0.3, 'Exponential'}, {
                Size = udim2(0, 238, 0, 30),
                Position = udim2(0, 6, 0, 32),
            })
            ts(mainFrame.Title, {0.3, 'Exponential'}, {
                TextTransparency = 0
            })
            ts(mainFrame.CommandListFrame, {0.3, 'Exponential'}, {
                BackgroundTransparency = 0
            })
        end
    end
    local function close()
        if not cooldown then
            state = false
            ts(mainFrame, {0.3, 'Exponential'}, {
                Size = udim2(0, 200, 0, 30),
                Position = udim2(0, mainFrame.AbsolutePosition.X + 20, 0, mainFrame.AbsolutePosition.Y + 30)
            })
            mainFrame.TextFieldFrame.TextField.Text = ''
            ts(mainFrame.TextFieldFrame, {0.3, 'Exponential'}, {
                Size = udim2(0, 192, 0, 22),
                Position = udim2(0, 4, 0, 4),
            })
            ts(mainFrame.Title, {0.3, 'Exponential'}, {
                TextTransparency = 1
            })
            ts(mainFrame.CommandListFrame, {0.3, 'Exponential'}, {
                BackgroundTransparency = 1
            })
        end
    end

    local function adminActive()
        if mouse.X > mainFrame.AbsolutePosition.X and mouse.X < (mainFrame.AbsolutePosition.X + mainFrame.AbsoluteSize.X) and mouse.Y > mainFrame.AbsolutePosition.Y and mouse.Y < (mainFrame.AbsolutePosition.Y + mainFrame.AbsoluteSize.Y) then
            return true
        end
        return false
    end

    local function executeCommand(input, command, callback)
        input = input:gsub(command, '');
        input = input:sub(2, #input);
        if typeof(callback) ~= 'function' then
            callback = function() end;
        end
        callback(unpack(input:split(' ')));
    end
    mainFrame.TextFieldFrame.TextField.FocusLost:connect(function(enterPressed)
        if enterPressed then
            pcall(function()
                local text = mainFrame.TextFieldFrame.TextField.Text
                local split = text:split(' ')
                local args = {
                    text,
                    text:split(' ')[1],
                    commands[text:split(' ')[1]].Callback                
                }
                executeCommand(args[1], args[2], args[3]);
            end)
            wait()
            mainFrame.TextFieldFrame.TextField.Text = ''
        else
            mainFrame.TextFieldFrame.TextField.Text = ''
        end
    end)

    local descFrame = instance('Frame', {
        Parent = sgui,
        Size = udim2(0, 100, 0, 50),
        Name = 'CommandDetails',
        BackgroundColor3 = theme.BodyColor,
    }, {
        instance('UICorner', {
            CornerRadius = UDim.new(0, 4)
        }),
        instance('Frame', {
            Name = 'Container',
            Size = udim2(1, -8, 1, -8),
            Position = udim2(0, 4, 0, 4),
            BackgroundColor3 = theme.TextFieldFrame
        }, {
            instance('UICorner', {
                CornerRadius = UDim.new(0, 4)
            }),
            instance('TextLabel', {
                Name = 'CommandName', 
                BackgroundTransparency = 1,
                Text = '??????',
                Font = 'GothamSemibold',
                TextColor3 = theme.TextColor,
                TextSize = 14,
                Position = udim2(0, 8, 0, 3),
                Size = udim2(1, -8, 0, 20),
                TextXAlignment = 'Left'
            }),
            instance('TextLabel', {
                Name = 'CommandDescription',
                BackgroundTransparency = 1,
                Text = '??????????????',
                Font = 'Gotham',
                TextColor3 = theme.PlaceholderTextColor,
                TextSize = 12,
                Position = udim2(0, 4, 0, 22),
                Size = udim2(1, -4, 0, 20),
                TextXAlignment = 'Left',
            })
        })
    })
    local function commandListActive()
        if adminActive() then
            if mouse.X > mainFrame.CommandListFrame.AbsolutePosition.X and mouse.X < (mainFrame.CommandListFrame.AbsolutePosition.X + mainFrame.CommandListFrame.AbsoluteSize.X) and mouse.Y > mainFrame.CommandListFrame.AbsolutePosition.Y and mouse.Y < (mainFrame.CommandListFrame.AbsolutePosition.Y + mainFrame.CommandListFrame.AbsoluteSize.Y) then
                return true
            end
        end
        return false
    end
    spawn(function()
        while true do
            wait() 
            ts(descFrame, {0.3, 'Exponential'}, {
                BackgroundTransparency = commandListActive() and 0 or 1
            })
            ts(descFrame.Container, {0.3, 'Exponential'}, {
                BackgroundTransparency = commandListActive() and 0 or 1
            })
            ts(descFrame.Container.CommandName, {0.3, 'Exponential'}, {
                TextTransparency = commandListActive() and 0 or 1
            })
            ts(descFrame.Container.CommandDescription, {0.3, 'Exponential'}, {
                TextTransparency = commandListActive() and 0 or 1
            })
        end
    end)
    local function updateDesc(name, desc)
        local textService = service('TextService')
        local nameSize, descSize = textService:GetTextSize(name, 14, 'GothamSemibold', Vector2.new(math.huge, 20)), textService:GetTextSize(desc, 12, 'Gotham', Vector2.new(math.huge, 20))
        local relativeSize = (nameSize.X > descSize.X and nameSize.X or descSize.X) + (nameSize.X > descSize.X and 25 or 18)
        descFrame.Container.CommandName.Text = '??'
        descFrame.Container.CommandDescription.Text = '?????'
        descFrame.Size = udim2(0, relativeSize, 0, 50)
        descFrame.Container.CommandName.Text = name
        descFrame.Container.CommandDescription.Text = desc
    end
    mouse.Move:connect(function()
        descFrame.Position = udim2(0, mouse.X + 8, 0, mouse.Y + 20)
    end)

    local list = mainFrame.CommandListFrame.Commands
    local stringList = {}

    for a,v in next, data.Commands or {} do
        local newButton = instance('TextButton', {
            Parent = list,
            BackgroundTransparency = 1,
            TextSize = 12,
            Font = 'Gotham',
            Text = tostring(a),
            Size = udim2(1, 0, 0, 24),
            TextColor3 = theme.TextColor,
            TextXAlignment = 'Left',
            ClipsDescendants = true
        }, nil, {
            function(self)
                self.MouseEnter:connect(function()
                    updateDesc(tostring(a), v.Description)
                end)
                self.MouseButton1Down:connect(function()
                    mainFrame.TextFieldFrame.TextField.ClearTextOnFocus = false
                    mainFrame.TextFieldFrame.TextField.Text = tostring(a) .. ' '
                    mainFrame.TextFieldFrame.TextField:CaptureFocus()
                    mainFrame.TextFieldFrame.TextField.ClearTextOnFocus = true
                end)
            end
        })
        table.insert(stringList, #stringList + 1, {
            name = tostring(a),
            inst = newButton
        })
    end

    local function filter(text)
        if text ~= '' then
            for a,v in next, stringList do
                if not v.name:find(text) then
                    ts(v.inst, {0.3, 'Exponential'}, {
                        Size = udim2(1, 0, 0, 0)
                    })
                else
                    ts(v.inst, {0.3, 'Exponential'}, {
                        Size = udim2(1, 0, 0, 24)
                    })
                end
            end
        else
            for a,v in next, stringList do
                ts(v.inst, {0.3, 'Exponential'}, {
                    Size = udim2(1, 0, 0, 24)
                })
            end
        end
    end
    mainFrame.TextFieldFrame.TextField:GetPropertyChangedSignal('Text'):Connect(function()
        filter(mainFrame.TextFieldFrame.TextField.Text)
    end)

    local uis = service('UserInputService')
    uis.InputBegan:connect(function(k, t)
        if t then 
            return
        end
        if k.KeyCode == Enum.KeyCode.Comma then
            mainFrame.TextFieldFrame.TextField:CaptureFocus()
            wait()
            mainFrame.TextFieldFrame.TextField.Text = ''
        end
    end)

    spawn(function()
        while true do
            wait()
            if adminActive() and state == false or mainFrame.TextFieldFrame.TextField:IsFocused() and state == false then
                open()
            elseif state == true and not adminActive() and not mainFrame.TextFieldFrame.TextField:IsFocused() then
                close()
            end
        end
    end)
end

return admin
