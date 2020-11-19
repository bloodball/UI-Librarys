--PayPal Tools is a GUI for jailbreak made by 'Haze'.

local library = {}

function dragify(Frame)
    dragToggle = nil
    dragSpeed = .25
    dragInput = nil
    dragStart = nil
    dragPos = nil
    
    function updateInput(input)
        Delta = input.Position - dragStart
        Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + Delta.X, startPos.Y.Scale, startPos.Y.Offset + Delta.Y)
        game:GetService("TweenService"):Create(Frame, TweenInfo.new(.25), {Position = Position}):Play()
    end
    
    Frame.InputBegan:Connect(function(input)
        if (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) then
            dragToggle = true
            dragStart = input.Position
            startPos = Frame.Position
            input.Changed:Connect(function()
                if (input.UserInputState == Enum.UserInputState.End) then
                    dragToggle = false
                end
            end)
        end
    end)
    
    Frame.InputChanged:Connect(function(input)
        if (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
            dragInput = input
        end
    end)
    
    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if (input == dragInput and dragToggle) then
            updateInput(input)
        end
    end)
end

function library:CreateFrame()
    local PayPal = Instance.new("ScreenGui")
    local Frame = Instance.new("ImageLabel")
    local TabFrame = Instance.new("TextLabel")
    local TabFrameRound = Instance.new("ImageLabel")
    local UIListLayout = Instance.new("UIListLayout")
    local Cent = Instance.new("TextLabel")
    local CentRound = Instance.new("ImageLabel")
    local Frame_2 = Instance.new("Frame")
    local UIGridLayout = Instance.new("UIGridLayout")
    local Name = Instance.new("TextLabel")
    local SubName = Instance.new("TextLabel")
    local Dis = Instance.new("TextLabel")

    PayPal.Name = "PayPal"
    PayPal.Parent = game.CoreGui

    Frame.Name = "Frame"
    Frame.Parent = PayPal
    Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    Frame.BackgroundTransparency = 1.000
    Frame.Position = UDim2.new(0, 9, 0, 669)
    Frame.Size = UDim2.new(0, 513, 0, 306)
    Frame.Image = "rbxassetid://3570695787"
    Frame.ImageColor3 = Color3.fromRGB(26, 26, 26)
    Frame.ScaleType = Enum.ScaleType.Slice
    Frame.SliceCenter = Rect.new(100, 100, 100, 100)
    Frame.SliceScale = 0.060
    dragify(Frame)

    TabFrame.Name = "TabFrame"
    TabFrame.Parent = Frame
    TabFrame.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
    TabFrame.BackgroundTransparency = 1.000
    TabFrame.BorderSizePixel = 0
    TabFrame.Position = UDim2.new(0.0358187146, 0, 0.349928945, 0)
    TabFrame.Size = UDim2.new(0, 160, 0, 182)
    TabFrame.Font = Enum.Font.SourceSans
    TabFrame.TextColor3 = Color3.fromRGB(0, 0, 0)
    TabFrame.TextSize = 14.000

    TabFrameRound.Name = "TabFrameRound"
    TabFrameRound.Parent = TabFrame
    TabFrameRound.AnchorPoint = Vector2.new(0.5, 0.5)
    TabFrameRound.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    TabFrameRound.BackgroundTransparency = 1.000
    TabFrameRound.Position = UDim2.new(0.474999994, 0, 0.442307681, 0)
    TabFrameRound.Size = UDim2.new(1.04999995, 0, 1.04945052, 0)
    TabFrameRound.Image = "rbxassetid://3570695787"
    TabFrameRound.ImageColor3 = Color3.fromRGB(22, 22, 22)
    TabFrameRound.ScaleType = Enum.ScaleType.Slice
    TabFrameRound.SliceCenter = Rect.new(100, 100, 100, 100)
    TabFrameRound.SliceScale = 0.060

    UIListLayout.Parent = TabFrameRound
    UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder

    

    Cent.Name = "Cent"
    Cent.Parent = Frame
    Cent.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
    Cent.BackgroundTransparency = 1.000
    Cent.BorderSizePixel = 0
    Cent.Position = UDim2.new(0.378520161, 0, 0.0137203038, 0)
    Cent.Size = UDim2.new(0, 318, 0, 297)
    Cent.Font = Enum.Font.SourceSans
    Cent.TextColor3 = Color3.fromRGB(0, 0, 0)
    Cent.TextSize = 14.000

    CentRound.Name = "CentRound"
    CentRound.Parent = Cent
    CentRound.AnchorPoint = Vector2.new(0.5, 0.5)
    CentRound.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    CentRound.BackgroundTransparency = 1.000
    CentRound.Position = UDim2.new(0.483999997, 0, 0.5, 0)
    CentRound.Size = UDim2.new(1, 0, 1, 0)
    CentRound.Image = "rbxassetid://3570695787"
    CentRound.ImageColor3 = Color3.fromRGB(22, 22, 22)
    CentRound.ScaleType = Enum.ScaleType.Slice
    CentRound.SliceCenter = Rect.new(100, 100, 100, 100)
    CentRound.SliceScale = 0.060

    Frame_2.Parent = Cent
    Frame_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    Frame_2.BackgroundTransparency = 1.000
    Frame_2.Position = UDim2.new(0.00601253891, 0, 0.0127278855, 0)
    Frame_2.Size = UDim2.new(0, 305, 0, 289)

    UIGridLayout.Parent = Frame_2
    UIGridLayout.SortOrder = Enum.SortOrder.LayoutOrder
    UIGridLayout.CellSize = UDim2.new(0, 150, 0, 40)

    Name.Name = "Name"
    Name.Parent = Frame
    Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    Name.BackgroundTransparency = 1.000
    Name.BorderColor3 = Color3.fromRGB(27, 42, 53)
    Name.Position = UDim2.new(0.00462962966, 0, 0.013001984, 0)
    Name.Size = UDim2.new(0, 183, 0, 50)
    Name.Font = Enum.Font.GothamBold
    Name.Text = "PayPal"
    Name.TextColor3 = Color3.fromRGB(0, 170, 255)
    Name.TextSize = 25.000

    SubName.Name = "Sub Name"
    SubName.Parent = Frame
    SubName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    SubName.BackgroundTransparency = 1.000
    SubName.BorderColor3 = Color3.fromRGB(27, 42, 53)
    SubName.Position = UDim2.new(0.00657894742, 0, 0.15536508, 0)
    SubName.Size = UDim2.new(0, 177, 0, 19)
    SubName.Font = Enum.Font.GothamBold
    SubName.Text = "Tools"
    SubName.TextColor3 = Color3.fromRGB(255, 255, 255)
    SubName.TextSize = 20.000

    Dis.Name = "Dis"
    Dis.Parent = Frame
    Dis.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    Dis.BackgroundTransparency = 1.000
    Dis.Position = UDim2.new(0.0199999996, 0, 0.935000002, 0)
    Dis.Size = UDim2.new(0, 168, 0, 14)
    Dis.Font = Enum.Font.GothamSemibold
    Dis.Text = "invite.gg/paypaljailbreak"
    Dis.TextColor3 = Color3.fromRGB(255, 255, 255)
    Dis.TextSize = 12.000

    local UtilsLib = {}

    function UtilsLib:CreateLabel(text)
        local Label = Instance.new("TextLabel")
        Label.Name = "Label"
        Label.Parent = TabFrameRound
        Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Label.BackgroundTransparency = 1.000
        Label.Position = UDim2.new(-0.0297619049, 0, 0.10047847, 0)
        Label.Size = UDim2.new(0, 164, 0, 31)
        Label.Font = Enum.Font.GothamSemibold
        Label.Text = text
        Label.TextColor3 = Color3.fromRGB(255, 255, 255)
        Label.TextSize = 16.000
    end

    function UtilsLib:CreateToggle(text, value, callback)
        local enabled = value
        local Toggle = Instance.new("TextLabel")
        local ToggleName = Instance.new("TextLabel")
        local Toggle_Roundify_4px = Instance.new("ImageLabel")
        local ToggleButton = Instance.new("TextButton")
        local Blue = Instance.new("ImageLabel")
        local Grey = Instance.new("ImageLabel")

        Toggle.Name = "Toggle"
        Toggle.Parent = Frame_2
        Toggle.BackgroundColor3 = Color3.fromRGB(26, 26, 26)
        Toggle.BackgroundTransparency = 1.000
        Toggle.BorderSizePixel = 0
        Toggle.Size = UDim2.new(0, 200, 0, 50)
        Toggle.Font = Enum.Font.SourceSans
        Toggle.Text = ""
        Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)
        Toggle.TextSize = 14.000

        ToggleName.Name = "Toggle Name"
        ToggleName.Parent = Toggle
        ToggleName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        ToggleName.BackgroundTransparency = 1.000
        ToggleName.BorderColor3 = Color3.fromRGB(27, 42, 53)
        ToggleName.Position = UDim2.new(0.0122013343, 0, 0.0806037933, 0)
        ToggleName.Size = UDim2.new(0, 128, 0, 32)
        ToggleName.ZIndex = 4
        ToggleName.Font = Enum.Font.GothamSemibold
        ToggleName.Text = text
        ToggleName.TextColor3 = Color3.fromRGB(255, 255, 255)
        ToggleName.TextSize = 14.000

        Toggle_Roundify_4px.Name = "Toggle_Roundify_4px"
        Toggle_Roundify_4px.Parent = Toggle
        Toggle_Roundify_4px.AnchorPoint = Vector2.new(0.5, 0.5)
        Toggle_Roundify_4px.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Toggle_Roundify_4px.BackgroundTransparency = 1.000
        Toggle_Roundify_4px.Position = UDim2.new(0.5, 0, 0.5, 0)
        Toggle_Roundify_4px.Size = UDim2.new(1, 0, 1, 0)
        Toggle_Roundify_4px.Image = "rbxassetid://3570695787"
        Toggle_Roundify_4px.ImageColor3 = Color3.fromRGB(26, 26, 26)
        Toggle_Roundify_4px.ScaleType = Enum.ScaleType.Slice
        Toggle_Roundify_4px.SliceCenter = Rect.new(100, 100, 100, 100)
        Toggle_Roundify_4px.SliceScale = 0.040

        ToggleButton.Name = "ToggleButton"
        ToggleButton.Parent = Toggle
        ToggleButton.BackgroundColor3 = Color3.fromRGB(81, 81, 81)
        ToggleButton.BackgroundTransparency = 1.000
        ToggleButton.BorderSizePixel = 0
        ToggleButton.Position = UDim2.new(0.801886797, 0, 0.255603641, 0)
        ToggleButton.Size = UDim2.new(0, 17, 0, 17)
        ToggleButton.ZIndex = 2
        ToggleButton.Font = Enum.Font.SourceSans
        ToggleButton.Text = ""
        ToggleButton.TextColor3 = Color3.fromRGB(0, 0, 0)
        ToggleButton.TextSize = 14.000

        Blue.Name = "Blue"
        Blue.Parent = ToggleButton
        Blue.Active = true
        Blue.AnchorPoint = Vector2.new(0.5, 0.5)
        Blue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Blue.BackgroundTransparency = 1.000
        Blue.Position = UDim2.new(0.5, 0, 0.5, 0)
        Blue.Selectable = true
        Blue.Size = UDim2.new(1, 0, 1, 0)
        Blue.Visible = false
        Blue.Image = "rbxassetid://3570695787"
        Blue.ImageColor3 = Color3.fromRGB(0, 170, 255)
        Blue.ScaleType = Enum.ScaleType.Slice
        Blue.SliceCenter = Rect.new(100, 100, 100, 100)
        Blue.SliceScale = 0.040

        Grey.Name = "Grey"
        Grey.Parent = ToggleButton
        Grey.Active = true
        Grey.AnchorPoint = Vector2.new(0.5, 0.5)
        Grey.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Grey.BackgroundTransparency = 1.000
        Grey.Position = UDim2.new(0.5, 0, 0.5, 0)
        Grey.Selectable = true
        Grey.Size = UDim2.new(1, 0, 1, 0)
        Grey.Image = "rbxassetid://3570695787"
        Grey.ImageColor3 = Color3.fromRGB(81, 81, 81)
        Grey.ScaleType = Enum.ScaleType.Slice
        Grey.SliceCenter = Rect.new(100, 100, 100, 100)
        Grey.SliceScale = 0.040

        if enabled then
            Grey.Visible = false
            Blue.Visible = true
        else
            Grey.Visible = true
            Blue.Visible = false
        end

        function click()
            enabled = not enabled
            Blue.Visible = enabled
            Grey.Visible = not enabled
            pcall(callback, enabled)
        end

        ToggleButton.MouseButton1Click:Connect(click)

    end

    function UtilsLib:CreateTextBox()
        local TextBox = Instance.new("TextBox")
        local TextBox_Roundify_4px = Instance.new("ImageLabel")

        TextBox.Parent = Frame_2
        TextBox.BackgroundColor3 = Color3.fromRGB(26, 26, 26)
        TextBox.BackgroundTransparency = 1.000
        TextBox.BorderSizePixel = 0
        TextBox.Size = UDim2.new(0, 200, 0, 50)
        TextBox.ZIndex = 2
        TextBox.Font = Enum.Font.GothamSemibold
        TextBox.Text = "PlayerName"
        TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
        TextBox.TextSize = 13.000
        
        TextBox_Roundify_4px.Name = "TextBox_Roundify_4px"
        TextBox_Roundify_4px.Parent = TextBox
        TextBox_Roundify_4px.Active = true
        TextBox_Roundify_4px.AnchorPoint = Vector2.new(0.5, 0.5)
        TextBox_Roundify_4px.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        TextBox_Roundify_4px.BackgroundTransparency = 1.000
        TextBox_Roundify_4px.Position = UDim2.new(0.5, 0, 0.5, 0)
        TextBox_Roundify_4px.Selectable = true
        TextBox_Roundify_4px.Size = UDim2.new(1, 0, 1, 0)
        TextBox_Roundify_4px.Image = "rbxassetid://3570695787"
        TextBox_Roundify_4px.ImageColor3 = Color3.fromRGB(26, 26, 26)
        TextBox_Roundify_4px.ScaleType = Enum.ScaleType.Slice
        TextBox_Roundify_4px.SliceCenter = Rect.new(100, 100, 100, 100)
        TextBox_Roundify_4px.SliceScale = 0.040
    end
    return UtilsLib
end
return library
