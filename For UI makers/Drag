function dragify(Frame)
dragToggle = nil
dragSpeed = .25 -- You can edit this.
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
