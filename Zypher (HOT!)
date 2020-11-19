--[[

    _____                  _                   
   |__  /  _   _   _ __   | |__     ___   _ __ 
     / /  | | | | | '_ \  | '_ \   / _ \ | '__|
    / /_  | |_| | | |_) | | | | | |  __/ | |   
   /____|  \__, | | .__/  |_| |_|  \___| |_|   
           |___/  |_|                          

   Made by: xTheAlex14#3200
   Design: inspiration from Luzu#0001
   
]]

local Library = {}
local Objects = {}

local Themes = {
	TextColor = Color3.fromRGB(255,255,255)
}

function Library:Create(what, propri)
	local instance = Instance.new(what)
	
	for i, v in next, propri do
		if instance[i] and propri ~= "Parent" then
			instance[i] = v
		end
	end
	
	return instance
end

local mouse = game.Players.LocalPlayer:GetMouse()
local UIS = game:GetService("UserInputService")
local TS = game:GetService("TweenService")
local RS = game:GetService("RunService")

function Library:CreateMain(Options)
	
	local nameforcheck = Options.projName
	local Main = {}
	local firstCategory = true
	
	Main.Screengui = Library:Create("ScreenGui", {
		Name = Options.projName,
		ZIndexBehavior = Enum.ZIndexBehavior.Global,
		ResetOnSpawn = false,
	})
	
	Main.Motherframe = Library:Create("Frame", {
		Name = "Motherframe",
		BackgroundColor3 = Color3.fromRGB(46, 46, 54),
		BorderSizePixel = 0,
		Position = UDim2.new(0.5, -400, 0.5, -225),
		Size = UDim2.new(0, 700, 0, 460),
	})

	-- Drag is not made by me
	
	local dragInput
	local dragStart
	local startPos
	
	local function update(input)
		local delta = input.Position - dragStart
		Main.Motherframe:TweenPosition(UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y), 'Out', 'Linear', 0.01, true)
	end
	
	Main.Motherframe.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 then
			dragging = true
			dragStart = input.Position
			startPos = Main.Motherframe.Position
			repeat
				wait()
			until input.UserInputState == Enum.UserInputState.End
			dragging = false
		end
	end)
	
	Main.Motherframe.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement then
			dragInput = input
		end
	end)
	
	game:GetService("UserInputService").InputChanged:Connect(function(input)
		if input == dragInput and dragging then
			update(input)
		end
	end)
	
	Main.Upline = Library:Create("Frame", {
		Name = "Upline",
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		BorderSizePixel = 0,
		Size = UDim2.new(1, 0, 0.00899999961, 0),
		ZIndex = 10,
	})
	
	Main.Uplinegradient = Library:Create("UIGradient", {
		Color = ColorSequence.new{
			ColorSequenceKeypoint.new(0.00, Color3.fromRGB(0, 183, 183)),
			ColorSequenceKeypoint.new(0.00, Color3.fromRGB(0, 248, 248)),
			ColorSequenceKeypoint.new(1.00, Color3.fromRGB(125, 92, 164))
		}
	})
	
	Main.Sidebar = Library:Create("ScrollingFrame", {
		Name = "Sidebar",
		Active = true,
		BackgroundColor3 = Color3.fromRGB(39, 38, 46),
		BorderSizePixel = 0,
		Position = UDim2.new(0, 0, 0.00899999309, 0),
		Size = UDim2.new(0.214041099, 0, 0.991376221, 0),
		CanvasSize = UDim2.new(0, 0, 0, 15),
		ScrollBarThickness = 0,
	})
	
	local Siderbarpadding = Library:Create("UIPadding", {
		PaddingLeft = UDim.new(0.047, 0),
		PaddingTop = UDim.new(0, 15)
	})
	
	Siderbarpadding.Parent = Main.Sidebar
	Siderbarpadding = nil
	
	Main.Categorieshandler = Library:Create("Frame", {
		Name = "Categories",
		BackgroundColor3 = Color3.fromRGB(46, 46, 54),
		BorderSizePixel = 0,
		Position = UDim2.new(0.214041084, 0, 0.00869414024, 0),
		Size = UDim2.new(0.784817278, 0, 0.991132021, 0),
	})
	
	Main.Categoriesselector = Library:Create("ImageLabel", {
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		BackgroundTransparency = 1.000,
		Position = UDim2.new(0, 0, 0, 0),
		Size = UDim2.new(0.95, 0, 0, 30),
		Image = "rbxassetid://3570695787",
		ImageColor3 = Color3.fromRGB(49, 49, 59),
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(100, 100, 100, 100),
		SliceScale = 0.04,
	})
	
	local textsize = 18
	
	if Options.Resizable then 
		
		local scaling = 18 / 460
		
		Main.ResizeBtn = Library:Create("TextButton", {
			Name = "ResizeButton",
			BackgroundColor3 = Color3.fromRGB(46, 46, 54),
			BorderSizePixel = 0,
			Position = UDim2.new(1, -20, 1, -20),
			Size = UDim2.new(0, 20, 0, 20),
			AutoButtonColor = false,
			Font = Enum.Font.SourceSans,
			Text = "",
			TextColor3 = Color3.fromRGB(0, 0, 0),
			TextSize = 14.000,
		})
		
		Main.ResizeBtn.Parent = Main.Motherframe
		
		local min = Options.MinSize
		local max = Options.MaxSize
		local connection
		local sP
		local MSS
		local size
		
		local function hasi(v, p)
			local x = v[p]
		end
		local function has(v, p)
			return pcall(function()
				hasi(v, p)
			end)
		end
		
		Main.ResizeBtn.MouseButton1Down:Connect(function()
			mouse.Icon = "http://www.roblox.com/asset/?id=1283244442"
			sP = Vector2.new(mouse.X, mouse.Y)
			MSS = Main.Motherframe.Size
			connection = RS.Heartbeat:Connect(function()
				if sP then
					local oldtextsize = textsize
					local distance = Vector2.new(mouse.X, mouse.Y) - sP;
					size = (MSS + UDim2.new(0, distance.X, 0, distance.Y))
					if (MSS + UDim2.new(0, distance.X, 0, distance.Y)).X.Offset <= min.X.Offset then
						size = UDim2.new(0, min.X.Offset, 0, size.Y.Offset)
					elseif (MSS + UDim2.new(0, distance.X, 0, distance.Y)).X.Offset >= max.X.Offset then
						size = UDim2.new(0, max.X.Offset, 0, size.Y.Offset)
					end
					
					if (MSS + UDim2.new(0, distance.X, 0, distance.Y)).Y.Offset <= min.Y.Offset then
						size = UDim2.new(0, size.X.Offset, 0, min.Y.Offset)
					elseif (MSS + UDim2.new(0, distance.X, 0, distance.Y)).Y.Offset >= max.Y.Offset then
						size = UDim2.new(0, size.X.Offset, 0, max.Y.Offset)
					end
					Main.Motherframe.Size = size
					textsize = math.floor(size.Y.Offset * scaling)
					if oldtextsize ~= textsize then
						for i, v in pairs (Main.Motherframe:GetDescendants()) do
							if v.Name ~= "Colorpicker" and has(v, "TextSize") then
								v.TextSize = textsize
							end
						end
					end
				end
			end)
			UIS.InputEnded:Connect(function(Check)
				if Check.UserInputType == Enum.UserInputType.MouseButton1 then
					if connection then
						connection:Disconnect()
						connection = nil
					end
					if mouse.Icon == "http://www.roblox.com/asset/?id=1283244442" then 
						mouse.Icon = ""
					end
				end
			end)
		end)
	end
	
	local CategoryDistanceCounter = 0
	
	function Main:CreateCategory(Name)
		
		local Category = {}
		
		Category.CButton = Library:Create("TextButton", {
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1.000,
			BorderSizePixel = 0,
			Position = UDim2.new(0.027, 0, 0, CategoryDistanceCounter),
			Size = UDim2.new(0.95, 0, 0, 30),
			ZIndex = 2,
			Font = Enum.Font.GothamBold,
			Text = Name,
			Name = Name,
			TextColor3 = Color3.fromRGB(255,255,255),
			TextSize = 18,
			TextWrapped = true,
			TextXAlignment = Enum.TextXAlignment.Left,
		})
		
		Category.Container = Library:Create("ScrollingFrame", {
			Name = Name.."Category",
			BackgroundColor3 = Color3.fromRGB(46, 46, 54),
			BorderSizePixel = 0,
			Size = UDim2.new(1, 0, 1, 0),
			CanvasSize = UDim2.new(0, 0, 0, 15),
			Visible = false,
			ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0),
			ScrollBarThickness = 4,
		})
		
		Category.CPadding = Library:Create("UIPadding", {
			PaddingLeft = UDim.new(0.026, 0),
			PaddingTop = UDim.new(0, 15),
		})
		
		Category.CLayout = Library:Create("UIListLayout", {
			SortOrder = Enum.SortOrder.LayoutOrder,
			Padding = UDim.new(0, 15),
		})
		
		if firstCategory then 
			Category.Container.Visible = true
		end
		
		Category.CButton.MouseButton1Click:Connect(function()
			TS:Create(Main.Categoriesselector, TweenInfo.new(0.08), {
				Position = Category.CButton.Position - UDim2.new(0.027, 0, 0, 0)
			}):Play()
			
			for i, v in pairs(Main.Categorieshandler:GetChildren()) do 
				if v:IsA("ScrollingFrame") then 
					v.Visible = false
				end  
			end
			
			Category.Container.Visible = true
		end)
		
		function Category:CreateSection(Name)
			
			local Section = {}
			
			Section.Container = Library:Create("ImageLabel", {
				Name = Name.."Section",
				BackgroundColor3 = Color3.fromRGB(255, 255, 255),
				BackgroundTransparency = 1.000,
				BorderSizePixel = 0,
				Position = UDim2.new(0.0272727273, 0, 0, 0),
				Size = UDim2.new(0.973, 0, 0, 35),
				Image = "rbxassetid://3570695787",
				ImageColor3 = Color3.fromRGB(39, 38, 46),
				ScaleType = Enum.ScaleType.Slice,
				SliceCenter = Rect.new(100, 100, 100, 100),
				SliceScale = 0.04,
			})
			
			Section.SectionPadding = Library:Create("UIPadding", {
				PaddingLeft = UDim.new(0.02, 0),
				PaddingBottom = UDim.new(0, 10),
			})
			
			Section.SectionLayout = Library:Create("UIListLayout", {
				SortOrder = Enum.SortOrder.LayoutOrder,
				Padding = UDim.new(0, 10),
			})
			
			Section.SectionName = Library:Create("TextLabel", {
				Name = "Name",
				BackgroundColor3 = Color3.fromRGB(255, 255, 255),
				BackgroundTransparency = 1.000,
				BorderSizePixel = 0,
				Position = UDim2.new(-0.00999999978, 0, 0, -10),
				Size = UDim2.new(0.38499999, 0, 0, 25),
				Font = Enum.Font.GothamBold,
				Text = Name,
				TextColor3 = Color3.fromRGB(255,255,255),
				TextSize = 18.000,
				TextXAlignment = Enum.TextXAlignment.Left,
				TextYAlignment = Enum.TextYAlignment.Bottom,
			})

			function Section:SetText(Text)
				Section.SectionName.Text = Text
			end
			
			Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 50)
			
			function Section:Create(Type, Name, CallBack, Options)
				
				local Interactables = {}
				
				if Type:lower() == "button" then 
					
					Interactables.ButtonFrame = Library:Create("Frame", {
						Name = Name.."Button",
						Active = true,
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderColor3 = Color3.fromRGB(27, 42, 53),
						Position = UDim2.new(0, -44, 0, -34),
						Selectable = true,
						Size = UDim2.new(0.982, 0, 0, 30),
					})
					
					Interactables.Button = Library:Create("ImageButton", {
						AnchorPoint = Vector2.new(0.5, 0.5),
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderColor3 = Color3.fromRGB(27, 42, 53),
						Position = UDim2.new(0.5, 0, 0.491, 0),
						Size = UDim2.new(1, 0, 0, 30),
						AutoButtonColor = false,
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.ButtonText = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.100000001, 0, 0, 0),
						Size = UDim2.new(0.8, 0, 0, 30),
						Font = Enum.Font.GothamBold,
						Text = Name,
						TextColor3 = Color3.fromRGB(255,255,255),
						TextSize = 18.000,
					})
		
					function Interactables:SetButtonText(Text)
						Interactables.ButtonText.Text = Text
					end
					
					Interactables.Button.MouseButton1Click:Connect(function()
						
						if Options then
							if Options.animated then 
								TS:Create(Interactables.Button, TweenInfo.new(0.06), {
									Size = UDim2.new(0.96, 0, 0, 25)
								}):Play()
								wait(.07)
								TS:Create(Interactables.Button, TweenInfo.new(0.06), {
									Size = UDim2.new(1, 0, 0, 30)
								}):Play()			
							end
						end
						
						if CallBack then 
							CallBack()
						end
						
					end)
					
					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 40)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 40)
					
					Interactables.ButtonFrame.Parent = Section.Container
					
					Interactables.Button.Parent = Interactables.ButtonFrame
					
					Interactables.ButtonText.Parent = Interactables.Button
					
				elseif Type:lower() == "slider" then 
					
					local Min = Options.min or 1
					local Max = Options.max or 0
					local MoveConnection
					local Value = 0
					
					Interactables.Slider = Library:Create("ImageLabel", {
						Name = Name.."Slider",
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderColor3 = Color3.fromRGB(27, 42, 53),
						Position = UDim2.new(0, 10, 0, 85),
						Selectable = true,
						Size = UDim2.new(0.982, 0, 0, 50),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.SliderName = Library:Create("TextLabel", {					
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0, 4, 0, 2),
						Size = UDim2.new(0, 200, 0, 30),
						Font = Enum.Font.GothamBold,
						Text = Name,
						TextColor3 = Color3.fromRGB(255,255,255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					
					Interactables.SliderValue = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.888, 0, 0, 6),
						Size = UDim2.new(0.088, 0, 0, 22),
						Font = Enum.Font.GothamBold,
						Text = Min,
						TextColor3 = Color3.fromRGB(255,255,255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Right,
					})
					
					Interactables.SliderBackInner = Library:Create("ImageButton", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						ClipsDescendants = true,
						Position = UDim2.new(0.0120000001, 0, 0, 32),
						Size = UDim2.new(0.974008501, 0, 0, 10),
						AutoButtonColor = false,
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(21, 21, 26),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.03,
						ZIndex = 1,
					})
					
					Interactables.SliderInner = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0, 0, 0, 1),
						Size = UDim2.new(0, 0, 0, 8),
						ZIndex = 1,
						Image = "rbxassetid://3570695787",
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.03,				
					})

					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 60)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 60)
					
					Interactables.Slider.Parent = Section.Container
					
					Interactables.SliderName.Parent = Interactables.Slider
					
					Interactables.SliderValue.Parent = Interactables.Slider
					
					Interactables.SliderBackInner.Parent = Interactables.Slider
					
					Interactables.SliderInner.Parent = Interactables.SliderBackInner

					if Options.default then 
						Interactables.SliderValue.Text = tostring(Options.default)
						if CallBack then
							CallBack(Options.default)
						end
						local s = (Options.default - Min) / (Max - Min)
						TS:Create(Interactables.SliderInner, TweenInfo.new(0.05), {
							Size = UDim2.new(s, 0, 0, 8)
						}):Play()
					end
					
					Interactables.SliderBackInner.MouseButton1Down:Connect(function()
						
						MoveConnection = RS.Heartbeat:Connect(function()
							local s = math.clamp(mouse.X - Interactables.SliderBackInner.AbsolutePosition.X, 0, Interactables.SliderBackInner.AbsoluteSize.X) / Interactables.SliderBackInner.AbsoluteSize.X
							if Options.precise then
								Value = string.format("%.1f", Min + ((Max - Min) * s))
							else
								Value = math.floor(Min + ((Max - Min) * s))
							end
							Interactables.SliderValue.Text = tostring(Value)
							
							if CallBack then
								CallBack(Value)
							end
							
							TS:Create(Interactables.SliderInner, TweenInfo.new(0.05), {
								Size = UDim2.new(s, 0, 0, 8)
							}):Play()
						end)
						
						UIS.InputEnded:Connect(function(Check)
							if Check.UserInputType == Enum.UserInputType.MouseButton1 then
								if MoveConnection then
									MoveConnection:Disconnect()
									MoveConnection = nil
								end
							end
						end)
						
                    end)
                    
                    function Interactables:ChangeValue(SliderValue)
                        if SliderValue < Max then 
                            local scale = (SliderValue - Min) / (Max - Min)
                            TS:Create(Interactables.SliderInner, TweenInfo.new(0.05), {
                                Size = UDim2.new(scale, 0, 0, 8)
                            }):Play()
                            if CallBack then 
                                CallBack(SliderValue)
                            end 
                            Interactables.SliderValue.Text = tostring(SliderValue)
                        elseif SliderValue > Max then 
                            TS:Create(Interactables.SliderInner, TweenInfo.new(0.05), {
                                Size = UDim2.new(0, 1, 0, 8)
                            }):Play()
                            if CallBack then 
                                CallBack(Max)
                            end 
                            Interactables.SliderValue.Text = tostring(SliderValue)
                        elseif SliderValue < Min then 
                            TS:Create(Interactables.SliderInner, TweenInfo.new(0.05), {
                                Size = UDim2.new(0, 0, 0, 8)
                            }):Play()
                            if CallBack then 
                                CallBack(Min)
                            end         
                            Interactables.SliderValue.Text = tostring(SliderValue)                
                        end
                    end
					
				elseif Type:lower() == "toggle" then 
					
					local State = false
					
					Interactables.Toggle = Library:Create("ImageButton", {
						Name = Name.."Toggle",
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1,
						BorderSizePixel = 0,
						Position = UDim2.new(0.00576804997, 0, 0.055555556, 0),
						Size = UDim2.new(0.981999993, 0, 0, 35),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.ToggleText = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1,
						BorderSizePixel = 0,
						Position = UDim2.new(0.00800000038, 0, 0.057, 0),
						Size = UDim2.new(0.399576753, 0, 0.857142866, 0),
						Font = Enum.Font.GothamBold,
						Text = Name,
						TextColor3 = Color3.fromRGB(255,255,255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					
					Interactables.ToggleBack = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1,
						Position = UDim2.new(1, -62, 0.114, 0),
						Size = UDim2.new(0, 56, 0, 26),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(21, 21, 26),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.ToggleShow = Library:Create("ImageLabel", {						
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1,
						Position = UDim2.new(0.0359999985, 0, 0.115000002, 0),
						Size = UDim2.new(0, 26, 0, 20),
						Image = "rbxassetid://3570695787",
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					if Options then 
						if Options.default then 
							State = true 
							TS:Create(Interactables.ToggleShow, TweenInfo.new(0.1), {
								Position = UDim2.new(0.53, 0, 0.115, 0)
							}):Play()
							if CallBack then 
								CallBack(State)
							end
						end
					end
					
					Interactables.Toggle.MouseButton1Click:Connect(function()
						State = not State 
						
						if State then 
							TS:Create(Interactables.ToggleShow, TweenInfo.new(0.1), {
								Position = UDim2.new(0.53, 0, 0.115, 0)
							}):Play()
						else
							TS:Create(Interactables.ToggleShow, TweenInfo.new(0.1), {
								Position = UDim2.new(0.036, 0, 0.115, 0)
							}):Play()
						end
						
						if CallBack then 
							CallBack(State)
						end
						
                    end)
                    
                    function Interactables:ChangeState(State)
                        if State then 
							TS:Create(Interactables.ToggleShow, TweenInfo.new(0.1), {
								Position = UDim2.new(0.53, 0, 0.115, 0)
                            }):Play()
                            if CallBack then 
								CallBack(State)
							end
						else
							TS:Create(Interactables.ToggleShow, TweenInfo.new(0.1), {
								Position = UDim2.new(0.036, 0, 0.115, 0)
                            }):Play()
                            if CallBack then 
								CallBack(State)
							end
						end 
                    end 
					
					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 45)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 45)
					
					Interactables.Toggle.Parent = Section.Container
					
					Interactables.ToggleText.Parent = Interactables.Toggle
					
					Interactables.ToggleBack.Parent = Interactables.Toggle
					
					Interactables.ToggleShow.Parent = Interactables.ToggleBack
					
				elseif Type:lower() == "textbox" then
					
					local Text
					local PlaceHolderText
					if Options then 
						if Options.text then 
							PlaceHolderText = Options.text
						end
					end
					
					Interactables.TextBox = Library:Create("ImageLabel", {
						Name = Name.."Textbox",
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.0192307699, 0, 0.467741936, 0),
						Size = UDim2.new(0.981999993, 0, 0, 35),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.TextBoxName = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 4, 0, 2),
						Size = UDim2.new(0.400000006, 0, 0, 30),
						Font = Enum.Font.GothamBold,
						Text = Name,
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					
					Interactables.TextBoxBack = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.587970376, 0, 0.114, 0),
						Selectable = true,
						Size = UDim2.new(0.400000006, 0, 0, 26),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(21, 21, 26),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.030,
					})
					
					Interactables.ActualTextBox = Library:Create("TextBox", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0.0500000007, 0, 0.0384615399, 0),
						Size = UDim2.new(0.920000017, 0, 0, 23),
						Font = Enum.Font.GothamBold,
						PlaceholderText = PlaceHolderText or "Text",
						Text = "",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 14.000,
						TextWrapped = true,
						TextXAlignment = Enum.TextXAlignment.Right,
					})
					
					Interactables.ActualTextBox.FocusLost:Connect(function()
						Text = Interactables.ActualTextBox.Text
						
						if CallBack then
							CallBack(Text)
						end
					end)
					
					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 45)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 45)
					
					Interactables.TextBox.Parent = Section.Container
					
					Interactables.TextBoxName.Parent = Interactables.TextBox
					
					Interactables.TextBoxBack.Parent = Interactables.TextBox
					
					Interactables.ActualTextBox.Parent = Interactables.TextBoxBack
					
				elseif Type:lower() == "textlabel" then 
					
					Interactables.TextLabelBox = Library:Create("ImageLabel", {
						Name = Name.."TextLabel",
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.0192307699, 0, 0.467741936, 0),
						Size = UDim2.new(0.982, 0, 0, 35),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.Textlabel = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0.008, 0, 0, 2),
						Size = UDim2.new(.991, 0, 0, 30),
						Font = Enum.Font.GothamBold,
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					
					if #Name <= 46 then
						Interactables.Textlabel.Text = Name
					end

					function Interactables:SetText(Text)
						if #Text <= 46 then 
							Interactables.Textlabel.Text = Text
						end
					end
					
					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 45)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 45)
					
					Interactables.TextLabelBox.Parent = Section.Container
					
					Interactables.Textlabel.Parent = Interactables.TextLabelBox
					
				elseif Type:lower() == "keybind" then 
					
					Interactables.KeyBindBox = Library:Create("ImageLabel", {
						Name = Name.."KeyBind",
						Active = true,
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderColor3 = Color3.fromRGB(27, 42, 53),
						Position = UDim2.new(0, 10, 0, 235),
						Selectable = true,
						Size = UDim2.new(0.981999993, 0, 0, 35),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.KeyBindName = Library:Create("TextLabel", {						
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.00800000038, 0, 0, 2),
						Size = UDim2.new(0.400000006, 0, 0, 30),
						Font = Enum.Font.GothamBold,
						Text = Name,
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					
					Interactables.KeyBindButton = Library:Create("ImageButton", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(1, -126, 0, 4),
						Size = UDim2.new(0, 120, 0, 26),
						AutoButtonColor = false,
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(21, 21, 26),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.KeyBindKey = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.64, -30, 0, 0),
						Size = UDim2.new(0, 30, 1, 0),
						Font = Enum.Font.GothamBold,
						Text = "None",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 18.000,
					})
					
					local connection
					local changing
					local bind
					local inputconnection
					local checkconnection
					
					if Options then
						if Options.default then 
							bind = Options.default
							Interactables.KeyBindKey.Text = bind.Name
						end
					end
					
					Interactables.KeyBindButton.MouseButton1Click:Connect(function()
						changing = true
						Interactables.KeyBindKey.Text = "..."
						connection = game:GetService("UserInputService").InputBegan:Connect(function(i)
							if i.UserInputType.Name == "Keyboard" and i.KeyCode ~= Enum.KeyCode.Backspace then
								Interactables.KeyBindKey.Text = i.KeyCode.Name
								bind = i.KeyCode
								if connection then
									connection:Disconnect()
									connection = nil
									wait(.1)
									changing = false
								end
							elseif i.KeyCode == Enum.KeyCode.Backspace then
								Interactables.KeyBindKey.Text = "None"
								bind = nil
								if connection then
									connection:Disconnect()
									connection = nil 
									wait(.1)
									changing = false
								end
							end
						end)
					end)
					
					inputconnection = game:GetService("UserInputService").InputBegan:Connect(function(i, GPE)
						if bind and i.KeyCode == bind and not GPE and not connection then
							if CallBack and not changing then
								CallBack(i.KeyCode)
							end
						end
					end)

					checkconnection = game:GetService("CoreGui").ChildRemoved:Connect(function(child)
						if child.Name == nameforcheck then 
							if inputconnection then
								inputconnection:Disconnect()
								inputconnection = nil
							end
							if checkconnection then 
								checkconnection:Disconnect()
								checkconnection = nil
							end 
						end 
					end)
					
					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 45)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 45)
					
					Interactables.KeyBindBox.Parent = Section.Container
					
					Interactables.KeyBindName.Parent = Interactables.KeyBindBox
					
					Interactables.KeyBindButton.Parent = Interactables.KeyBindBox
					
					Interactables.KeyBindKey.Parent = Interactables.KeyBindButton
					
				elseif Type:lower() == "dropdown" then 
					if Options and not Options.search then
						
						local selectedvalue
						
						if Options then
							if Options.default and Options.options and not Options.playerlist then
								selectedvalue = Options.default
							elseif Options.default and Options.options and Options.playerlist then
								selectedvalue = Options.default
							elseif not Options.default and Options.options and Options.playerlist then
								selectedvalue = Options.options[1]
							elseif not Options.default and Options.options and not Options.playerlist then
								selectedvalue = Options.options[1]
							elseif not Options.default and not Options.options and Options.playerlist then
								selectedvalue = game:GetService("Players"):GetChildren()[1].Name  
							elseif Options.default and not Options.options and not Options.playerlist then
								selectedvalue = Options.default      
							elseif Options.default and not Options.options and Options.playerlist then
								selectedvalue = Options.default               
							end
						end
						
						local tablelist
						
						if Options then
							if Options.options and not Options.playerlist then
								tablelist = Options.options
							elseif Options.options and Options.playerlist then
								tablelist = {}
								
								for g, f in pairs(Options.options) do
									table.insert(tablelist, f)
								end
								local list = game:GetService("Players"):GetChildren()
								if not Options.plotlist then
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
										end
									end
								else
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
											
											table.insert(tablelist, v.Name.."'s Plot")
										end
									end
								end
							elseif not Options.options and Options.playerlist then
								tablelist = {}
								local list = game:GetService("Players"):GetChildren()
								if not Options.plotlist then 
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
										end
									end     
								else       
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
											
											table.insert(tablelist, v.Name.."'s Plot")
										end
									end										
								end                        
							end
						end
						
						Interactables.dropdownb = Library:Create("ImageLabel", {
							Name = Name.."DropDown",
							BackgroundColor3 = Color3.fromRGB(255, 255, 255),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							Position = UDim2.new(0, 11, 0, 40),
							Size = UDim2.new(0.982, 0, 0, 30),
							ImageTransparency = 1,
							Image = "rbxassetid://3570695787",
							ImageColor3 = Color3.fromRGB(29, 29, 35),
							ScaleType = Enum.ScaleType.Slice,
							SliceCenter = Rect.new(100, 100, 100, 100),
							SliceScale = 0.040,
						})
						Interactables.dropdownb.ClipsDescendants = true
						
						Interactables.dropdown = Library:Create("ImageButton", {
							Name = Name.."DropDown",
							BackgroundColor3 = Color3.fromRGB(255, 255, 255),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							Position = UDim2.new(0, 0, 0, 0),
							Size = UDim2.new(1, 0, 0, 30),
							AutoButtonColor = false,
							Image = "rbxassetid://3570695787",
							ImageColor3 = Color3.fromRGB(29, 29, 35),
							ScaleType = Enum.ScaleType.Slice,
							SliceCenter = Rect.new(100, 100, 100, 100),
							SliceScale = 0.040,
						})
						
						Interactables.arrow = Library:Create("ImageLabel", {
							Name = "Arrow",
							Active = true,
							BackgroundColor3 = Color3.fromRGB(248, 248, 248),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							BorderSizePixel = 0,
							Position = UDim2.new(0.940401852, 0, 0.0333333351, 0),
							Rotation = 90.000,
							Selectable = true,
							Size = UDim2.new(0, 28, 0, 28),
							Image = "http://www.roblox.com/asset/?id=5054982349",
						})
						
						Interactables.selected = Library:Create("TextLabel", {
							Active = false,
							BackgroundColor3 = Color3.fromRGB(248, 248, 248),
							BackgroundTransparency = 1.000,
							BorderSizePixel = 0,
							Position = UDim2.new(0, 4, 0, 0),
							Selectable = false,
							Size = UDim2.new(0.200000003, 200, 1, 0),
							Font = Enum.Font.GothamBold,
							Text = tostring(selectedvalue),
							TextColor3 = Color3.fromRGB(255, 255, 255),
							TextSize = 18.000,
							TextXAlignment = Enum.TextXAlignment.Left,
						})
						
						Interactables.listb = Library:Create("ImageLabel", {
							Active = true,
							BackgroundColor3 = Color3.fromRGB(248, 248, 248),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							Position = UDim2.new(0, 0, 0, 40),
							Selectable = true,
							Size = UDim2.new(1, 0, 0, 120),
							ZIndex = 2,
							Image = "rbxassetid://3570695787",
							ImageColor3 = Color3.fromRGB(34, 34, 41),
							ScaleType = Enum.ScaleType.Slice,
							SliceCenter = Rect.new(100, 100, 100, 100),
							SliceScale = 0.040,
						})
						Interactables.list = Library:Create("ScrollingFrame", {
							Active = true,
							BackgroundColor3 = Color3.fromRGB(29, 29, 35),
							BackgroundTransparency = 1.000,
							BorderSizePixel = 0,
							Size = UDim2.new(1, 0, 1, 0),
							ZIndex = 2,
							CanvasSize = UDim2.new(0, 0, 0, 0),
							ScrollBarThickness = 0,
						})
						
						local tlistlayout = Library:Create("UIListLayout", {
							SortOrder = Enum.SortOrder.LayoutOrder,
							Padding = UDim.new(0, 10)
						})
						
						tlistlayout.Parent = Interactables.list
						tlistlayout = nil
						
						local tpadding = Library:Create("UIPadding", {
							PaddingBottom = UDim.new(0, 10),
							PaddingLeft = UDim.new(0, 10),
							PaddingTop = UDim.new(0, 10),
						})
						
						tpadding.Parent = Interactables.list
						tpadding = nil
						
						local dropdownopen = false
						
						Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 40)
						Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 40)
						
						Interactables.dropdownb.Parent = Section.Container
						Interactables.dropdown.Parent = Interactables.dropdownb
						Interactables.arrow.Parent = Interactables.dropdown
						Interactables.selected.Parent = Interactables.dropdown
						Interactables.listb.Parent = Interactables.dropdown
						Interactables.list.Parent = Interactables.listb
						
						local function refreshlist()
							
							for i, v in next, Interactables.list:GetChildren() do
								if v:IsA("ImageButton") then
									v:Destroy()
								end
							end
							
							for i, v in next, tablelist do
								local button = Library:Create("ImageButton", {
									Name = string.lower(v),
									AnchorPoint = Vector2.new(0.5, 0.5),
									BackgroundColor3 = Color3.fromRGB(255, 255, 255),
									BackgroundTransparency = 1.000,
									BorderColor3 = Color3.fromRGB(27, 42, 53),
									Position = UDim2.new(0, 252, 0, 0),
									Size = UDim2.new(0.98, 0, 0, 30),
									ZIndex = 2,
									AutoButtonColor = false,
									Image = "rbxassetid://3570695787",
									ImageColor3 = Color3.fromRGB(29, 29, 35),
									ScaleType = Enum.ScaleType.Slice,
									SliceCenter = Rect.new(100, 100, 100, 100),
									SliceScale = 0.040,
								})
								
								local buttontext = Library:Create("TextLabel", {
									BackgroundColor3 = Color3.fromRGB(255, 255, 255),
									BackgroundTransparency = 1.000,
									BorderSizePixel = 0,
									Position = UDim2.new(0.078, 0, 0, 0),
									Size = UDim2.new(0.833, 0, 1, 0),
									ZIndex = 2,
									Font = Enum.Font.GothamBold,
									Text = v,
									TextColor3 = Color3.fromRGB(255, 255, 255),
									TextSize = textsize,
								})
								
								button.Parent = Interactables.list
								buttontext.Parent = button
								
								button.MouseButton1Click:Connect(function()
									if dropdownopen then
										
										dropdownopen = not dropdownopen
										Interactables.selected.Text = v
										selectedvalue = v
										
										if dropdownopen then
											refreshlist()
											TS:Create(Section.Container, TweenInfo.new(0.1), {
												Size = Section.Container.Size + UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
												Size = UDim2.new(0.982, 0, 0, 154)
											}):Play()
											TS:Create(Category.Container, TweenInfo.new(0.1), {
												CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.list, TweenInfo.new(0.1), {
												CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
											}):Play()
											TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
												Rotation = 0
											}):Play()
										else
											refreshlist()
											TS:Create(Section.Container, TweenInfo.new(0.1), {
												Size = Section.Container.Size - UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
												Size = UDim2.new(0.982, 0, 0, 30)
											}):Play()
											TS:Create(Category.Container, TweenInfo.new(0.1), {
												CanvasSize = Category.Container.CanvasSize - UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
												Rotation = 90
											}):Play()
										end
										
										if CallBack then
											CallBack(selectedvalue)
										end
									end
								end)
							end
						end
						
						refreshlist()
						
						Interactables.dropdown.MouseButton1Click:Connect(function()
							dropdownopen = not dropdownopen
							
							if Options then
								if Options.options and not Options.playerlist then
									tablelist = Options.options
								elseif Options.options and Options.playerlist then
									tablelist = {}
									
									for g, f in pairs(Options.options) do
										table.insert(tablelist, f)
									end
									local list = game:GetService("Players"):GetChildren()
									if not Options.plotlist then
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
											end
										end
									else
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
												
												table.insert(tablelist, v.Name.."'s Plot")
											end
										end
									end
								elseif not Options.options and Options.playerlist then
									tablelist = {}
									local list = game:GetService("Players"):GetChildren()
									if not Options.plotlist then 
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
											end
										end     
									else       
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
												
												table.insert(tablelist, v.Name.."'s Plot")
											end
										end										
									end                        
								end
							end
							
							
							if dropdownopen then
								refreshlist()
								TS:Create(Section.Container, TweenInfo.new(0.1), {
									Size = Section.Container.Size + UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
									Size = UDim2.new(0.982, 0, 0, 154)
								}):Play()
								TS:Create(Category.Container, TweenInfo.new(0.1), {
									CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.list, TweenInfo.new(0.1), {
									CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
								}):Play()
								TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
									Rotation = 0
								}):Play()
							else
								refreshlist()
								TS:Create(Section.Container, TweenInfo.new(0.1), {
									Size = Section.Container.Size - UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
									Size = UDim2.new(0.982, 0, 0, 30)
								}):Play()
								TS:Create(Category.Container, TweenInfo.new(0.1), {
									CanvasSize = Category.Container.CanvasSize - UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
									Rotation = 90
								}):Play()
							end
							
						end)
					elseif Options and Options.search then
						
						local selectedvalue
						
						if Options then
							if Options.default and Options.options and not Options.playerlist then
								selectedvalue = Options.default
							elseif Options.default and Options.options and Options.playerlist then
								selectedvalue = Options.default
							elseif not Options.default and Options.options and Options.playerlist then
								selectedvalue = Options.options[1]
							elseif not Options.default and Options.options and not Options.playerlist then
								selectedvalue = Options.options[1]
							elseif not Options.default and not Options.options and Options.playerlist then
								selectedvalue = game:GetService("Players"):GetChildren()[1].Name  
							elseif Options.default and not Options.options and not Options.playerlist then
								selectedvalue = Options.default      
							elseif Options.default and not Options.options and Options.playerlist then
								selectedvalue = Options.default               
							end
						end
						
						local tablelist
						
						if Options then
							if Options.options and not Options.playerlist then
								tablelist = Options.options
							elseif Options.options and Options.playerlist then
								tablelist = {}
								
								for g, f in pairs(Options.options) do
									table.insert(tablelist, f)
								end
								local list = game:GetService("Players"):GetChildren()
								if not Options.plotlist then
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
										end
									end
								else
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
											
											table.insert(tablelist, v.Name.."'s Plot")
										end
									end
								end
							elseif not Options.options and Options.playerlist then
								tablelist = {}
								local list = game:GetService("Players"):GetChildren()
								if not Options.plotlist then 
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
										end
									end     
								else       
									for i, v in pairs(list) do
										if v:IsA("Player") then
											table.insert(tablelist, v.Name)
											
											table.insert(tablelist, v.Name.."'s Plot")
										end
									end										
								end                        
							end
						end
						
						Interactables.dropdownb = Library:Create("ImageLabel", {
							Name = Name.."DropDown",
							BackgroundColor3 = Color3.fromRGB(255, 255, 255),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							Position = UDim2.new(0, 11, 0, 40),
							Size = UDim2.new(0.982, 0, 0, 30),
							ImageTransparency = 1,
							Image = "rbxassetid://3570695787",
							ImageColor3 = Color3.fromRGB(29, 29, 35),
							ScaleType = Enum.ScaleType.Slice,
							SliceCenter = Rect.new(100, 100, 100, 100),
							SliceScale = 0.040,
						})
						Interactables.dropdownb.ClipsDescendants = true
						
						Interactables.dropdown = Library:Create("ImageButton", {
							Name = Name.."DropDown",
							BackgroundColor3 = Color3.fromRGB(255, 255, 255),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							Position = UDim2.new(0, 0, 0, 0),
							Size = UDim2.new(1, 0, 0, 30),
							AutoButtonColor = false,
							Image = "rbxassetid://3570695787",
							ImageColor3 = Color3.fromRGB(29, 29, 35),
							ScaleType = Enum.ScaleType.Slice,
							SliceCenter = Rect.new(100, 100, 100, 100),
							SliceScale = 0.040,
						})
						
						Interactables.arrow = Library:Create("ImageLabel", {
							Name = "Arrow",
							Active = true,
							BackgroundColor3 = Color3.fromRGB(248, 248, 248),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							BorderSizePixel = 0,
							Position = UDim2.new(1, -32, 0.0333333351, 0),
							Rotation = 90.000,
							Selectable = true,
							Size = UDim2.new(0, 28, 0, 28),
							Image = "http://www.roblox.com/asset/?id=5054982349",
						})
						
						Interactables.selected = Library:Create("TextBox", {
							Active = false,
							BackgroundColor3 = Color3.fromRGB(248, 248, 248),
							BackgroundTransparency = 1.000,
							BorderSizePixel = 0,
							Position = UDim2.new(0.008, 0, 0, 0),
							Selectable = false,
							Size = UDim2.new(0.65, 0, 1, 0),
							Font = Enum.Font.GothamBold,
							Text = tostring(selectedvalue),
							TextColor3 = Color3.fromRGB(255, 255, 255),
							TextSize = 18.000,
							TextXAlignment = Enum.TextXAlignment.Left,
						})
						
						Interactables.listb = Library:Create("ImageLabel", {
							Active = true,
							BackgroundColor3 = Color3.fromRGB(248, 248, 248),
							BackgroundTransparency = 1.000,
							BorderColor3 = Color3.fromRGB(27, 42, 53),
							Position = UDim2.new(0, 0, 0, 40),
							Selectable = true,
							Size = UDim2.new(1, 0, 0, 120),
							ZIndex = 2,
							Image = "rbxassetid://3570695787",
							ImageColor3 = Color3.fromRGB(34, 34, 41),
							ScaleType = Enum.ScaleType.Slice,
							SliceCenter = Rect.new(100, 100, 100, 100),
							SliceScale = 0.040,
						})
						Interactables.list = Library:Create("ScrollingFrame", {
							Active = true,
							BackgroundColor3 = Color3.fromRGB(29, 29, 35),
							BackgroundTransparency = 1.000,
							BorderSizePixel = 0,
							Size = UDim2.new(1, 0, 1, 0),
							ZIndex = 2,
							CanvasSize = UDim2.new(0, 0, 0, 0),
							ScrollBarThickness = 0,
						})
						
						local tlistlayout = Library:Create("UIListLayout", {
							SortOrder = Enum.SortOrder.LayoutOrder,
							Padding = UDim.new(0, 10)
						})
						
						tlistlayout.Parent = Interactables.list
						tlistlayout = nil
						
						local tpadding = Library:Create("UIPadding", {
							PaddingBottom = UDim.new(0, 10),
							PaddingLeft = UDim.new(0, 10),
							PaddingTop = UDim.new(0, 10),
						})
						
						local dropdownopen = false
						
						tpadding.Parent = Interactables.list
						tpadding = nil
						
						Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 40)
						Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 40)
						
						Interactables.dropdownb.Parent = Section.Container
						Interactables.dropdown.Parent = Interactables.dropdownb
						Interactables.arrow.Parent = Interactables.dropdown
						Interactables.selected.Parent = Interactables.dropdown
						Interactables.listb.Parent = Interactables.dropdown
						Interactables.list.Parent = Interactables.listb
						
						local function refreshlist()
							
							for i, v in next, Interactables.list:GetChildren() do
								if v:IsA("ImageButton") then
									v:Destroy()
								end
							end
							
							for i, v in next, tablelist do
								local button = Library:Create("ImageButton", {
									Name = string.lower(v),
									AnchorPoint = Vector2.new(0.5, 0.5),
									BackgroundColor3 = Color3.fromRGB(255, 255, 255),
									BackgroundTransparency = 1.000,
									BorderColor3 = Color3.fromRGB(27, 42, 53),
									Position = UDim2.new(0, 252, 0, 0),
									Size = UDim2.new(0.98, 0, 0, 30),
									ZIndex = 2,
									AutoButtonColor = false,
									Image = "rbxassetid://3570695787",
									ImageColor3 = Color3.fromRGB(29, 29, 35),
									ScaleType = Enum.ScaleType.Slice,
									SliceCenter = Rect.new(100, 100, 100, 100),
									SliceScale = 0.040,
								})
								
								local buttontext = Library:Create("TextLabel", {
									BackgroundColor3 = Color3.fromRGB(255, 255, 255),
									BackgroundTransparency = 1.000,
									BorderSizePixel = 0,
									Position = UDim2.new(0.078, 0, 0, 0),
									Size = UDim2.new(0.833, 0, 1, 0),
									ZIndex = 2,
									Font = Enum.Font.GothamBold,
									Text = v,
									TextColor3 = Color3.fromRGB(255, 255, 255),
									TextSize = textsize,
								})
								
								button.Parent = Interactables.list
								buttontext.Parent = button
								
								button.MouseButton1Click:Connect(function()
									if dropdownopen then
										
										dropdownopen = not dropdownopen
										Interactables.selected.Text = v
										selectedvalue = v

										
										
										if dropdownopen then
											refreshlist()
											TS:Create(Section.Container, TweenInfo.new(0.1), {
												Size = Section.Container.Size + UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
												Size = UDim2.new(0.982, 0, 0, 154)
											}):Play()
											TS:Create(Category.Container, TweenInfo.new(0.1), {
												CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.list, TweenInfo.new(0.1), {
												CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
											}):Play()
											TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
												Rotation = 0
											}):Play()
										else
											refreshlist()
											TS:Create(Section.Container, TweenInfo.new(0.1), {
												Size = Section.Container.Size - UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
												Size = UDim2.new(0.982, 0, 0, 30)
											}):Play()
											TS:Create(Category.Container, TweenInfo.new(0.1), {
												CanvasSize = Category.Container.CanvasSize - UDim2.new(0, 0, 0, 125)
											}):Play()
											TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
												Rotation = 90
											}):Play()
										end
										
										if CallBack then
											CallBack(selectedvalue)
										end
									end
								end)
							end
						end
						
						refreshlist()
						
						Interactables.dropdown.MouseButton1Click:Connect(function()
							dropdownopen = not dropdownopen

							tablelist = {}

							if Options then
								if Options.options and not Options.playerlist then
									tablelist = Options.options
								elseif Options.options and Options.playerlist then
									tablelist = {}
									
									for g, f in pairs(Options.options) do
										table.insert(tablelist, f)
									end
									local list = game:GetService("Players"):GetChildren()
									if not Options.plotlist then
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
											end
										end
									else
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
												
												table.insert(tablelist, v.Name.."'s Plot")
											end
										end
									end
								elseif not Options.options and Options.playerlist then
									tablelist = {}
									local list = game:GetService("Players"):GetChildren()
									if not Options.plotlist then 
										for i, v in pairs(list) do
											if v:IsA("Player") then
												print(v)
												table.insert(tablelist, v.Name)
											end
										end     
									else       
										for i, v in pairs(list) do
											if v:IsA("Player") then
												table.insert(tablelist, v.Name)
												
												table.insert(tablelist, v.Name.."'s Plot")
											end
										end										
									end                        
								end
							end
							
							
							if dropdownopen then
								refreshlist()
								TS:Create(Section.Container, TweenInfo.new(0.1), {
									Size = Section.Container.Size + UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
									Size = UDim2.new(0.982, 0, 0, 154)
								}):Play()
								TS:Create(Category.Container, TweenInfo.new(0.1), {
									CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.list, TweenInfo.new(0.1), {
									CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
								}):Play()
								TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
									Rotation = 0
								}):Play()
							else
								refreshlist()
								TS:Create(Section.Container, TweenInfo.new(0.1), {
									Size = Section.Container.Size - UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.dropdownb, TweenInfo.new(0.1), {
									Size = UDim2.new(0.982, 0, 0, 30)
								}):Play()
								TS:Create(Category.Container, TweenInfo.new(0.1), {
									CanvasSize = Category.Container.CanvasSize - UDim2.new(0, 0, 0, 125)
								}):Play()
								TS:Create(Interactables.arrow, TweenInfo.new(0.1), {
									Rotation = 90
								}):Play()
							end
							
						end)
						
						local Found = {}
						local searchtable = {}
						
						for i, v in pairs(tablelist) do
							table.insert(searchtable, string.lower(v))
						end
						
						local function Edit()
							for i in pairs(Found) do
								Found[i] = nil
							end
							for h, l in pairs(Interactables.list:GetChildren()) do
								if not l:IsA("UIListLayout") and not l:IsA("UIPadding") then
									l.Visible = false
								end
							end
							Interactables.selected.Text = string.lower(Interactables.selected.Text)
						end
						
						local function Search()
							local Results = {}
							local num
							for i, v in pairs(searchtable) do
								if string.find(v, Interactables.selected.Text) then
									table.insert(Found, v)
								end
							end
							for a, b in pairs(Interactables.list:GetChildren()) do
								for c, d in pairs(Found) do
									if d == b.Name then
										b.Visible = true
									end
								end
							end
							for p, n in pairs(Interactables.list:GetChildren()) do
								if not n:IsA("UIListLayout") and not n:IsA("UIPadding") and n.Visible == true then
									table.insert(Results, n)
									for c, d in pairs(Results) do
										num = c
									end
								end
							end
							if num ~= nil then
								num = num * 40
								Interactables.list.CanvasSize = UDim2.new(0, 0, 0, num) + UDim2.new(0, 0, 0, 20)
								num = 0
							end
						end
						
						local function Nil()
							for i, v in pairs(Interactables.list:GetChildren()) do
								if not v:IsA("UIListLayout") and not v:IsA("UIPadding") and v.Visible == false then
									TS:Create(Interactables.list, TweenInfo.new(0.1), {
										CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
									}):Play()
									v.Visible = true
								end 
							end
						end
						
						
						local SearchLock = true
						Interactables.selected.Changed:connect(function()
							if not SearchLock then
								Edit()
								Search()
							end
							if Interactables.selected.Text == "" then
								Nil()
								TS:Create(Interactables.list, TweenInfo.new(0.1), {
									CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
								}):Play()
							end
						end)
						
						
						Interactables.selected.FocusLost:connect(function()
							SearchLock = true
							if Interactables.selected.Text == "" then
								TS:Create(Interactables.list, TweenInfo.new(0.1), {
									CanvasSize = UDim2.new(0, 0, 0, Interactables.list["UIListLayout"].AbsoluteContentSize.Y) + UDim2.new(0, 0, 0, 26)
								}):Play()
								SearchLock = true
								Nil()
								Interactables.selected.Text = tostring(Options.default) or tostring(selectedvalue)
							end
						end)
						
						Interactables.selected.Focused:connect(function()
							SearchLock = false
						end)
					end
					
				elseif Type:lower() == "colorpicker" then 
					
					local colorpickeropen = false
					local colorpickervalue
					
					Interactables.colorpickerb = Library:Create("ImageButton", {
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderColor3 = Color3.fromRGB(27, 42, 53),
						Position = UDim2.new(0, 11, 0, 125),
						Size = UDim2.new(0.982, 0, 0, 35),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.colorpickertext = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.008, 0, 0, 2),
						Size = UDim2.new(0.4, 0, 0, 30),
						Font = Enum.Font.GothamBold,
						Text = Name,
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 18.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					Interactables.colorpickerbutton = Library:Create("ImageLabel", {
						Active = true,
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(1, -74, 0, 4),
						Selectable = true,
						Size = UDim2.new(0, 70, 0, 26),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(255, 0, 4),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.colorpickerframeb = Library:Create("Frame", {
						Name = "colorframe",
						BackgroundColor3 = Color3.fromRGB(46, 46, 54),
						BorderSizePixel = 0,
						Position = UDim2.new(1, 8, 0, 0),
						Size = UDim2.new(0, 0, 0, 205),
						BackgroundTransparency = 1,
					})
					Interactables.colorpickerframeb.ClipsDescendants = true
					
					Interactables.colorpickerframe = Library:Create("Frame", {
						BackgroundColor3 = Color3.fromRGB(46, 46, 54),
						BorderSizePixel = 0,
						Position = UDim2.new(0, 0, 0, 0),
						Size = UDim2.new(0, 190, 0, 205),                            
					})
					Interactables.colorpickerframe.ClipsDescendants = true
					
					Interactables.colorpickerupline = Library:Create("Frame", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BorderSizePixel = 0,
						Position = UDim2.new(0, 0, 0, 0),
						Size = UDim2.new(1, 0, 0, 4),
					})
					
					Interactables.colorpickeruplinegradient = Library:Create("UIGradient", {
						Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(0, 183, 183)), ColorSequenceKeypoint.new(0.00, Color3.fromRGB(0, 248, 248)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(125, 92, 164))},
					})
					
					Interactables.rback = Library:Create("ImageLabel", {
						Active = true,
						AnchorPoint = Vector2.new(0.5, 0.5),
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 35, 0, 165),
						Selectable = true,
						Size = UDim2.new(0, 50, 0, 20),
						ZIndex = 2,
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.rvalue = Library:Create("TextLabel", {
						Name = "Colorpicker",
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 18, 0, 3),
						Size = UDim2.new(0, 25, 0, 15),
						ZIndex = 2,
						Font = Enum.Font.GothamBold,
						Text = "255",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 11.000,
					})
					
					Interactables.rtext = Library:Create("TextLabel", {
						Name = "Colorpicker",
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 4, 0, 3),
						Size = UDim2.new(0, 15, 0, 15),
						ZIndex = 2,
						Font = Enum.Font.GothamBold,
						Text = "R:",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 14.000,
					})
					
					Interactables.gback = Library:Create("ImageLabel", {
						Active = true,
						AnchorPoint = Vector2.new(0.5, 0.5),
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.5, 0, 0, 165),
						Selectable = true,
						Size = UDim2.new(0, 50, 0, 20),
						ZIndex = 2,
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.gvalue = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 18, 0, 3),
						Size = UDim2.new(0, 25, 0, 15),
						ZIndex = 2,
						Name = "Colorpicker",
						Font = Enum.Font.GothamBold,
						Text = "255",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 11.000,
					})
					
					Interactables.gtext = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 4, 0, 3),
						Size = UDim2.new(0, 15, 0, 15),
						ZIndex = 2,
						Font = Enum.Font.GothamBold,
						Text = "G:",
						Name = "Colorpicker",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 14.000,
						TextWrapped = true,
					})
					
					Interactables.bback = Library:Create("ImageLabel", {
						Active = true,
						AnchorPoint = Vector2.new(0.5, 0.5),
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 155, 0, 165),
						Selectable = true,
						Size = UDim2.new(0, 50, 0, 20),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.bvalue = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 18, 0, 3),
						Size = UDim2.new(0, 25, 0, 15),
						ZIndex = 2,
						Font = Enum.Font.GothamBold,
						Text = "255",
						Name = "Colorpicker",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 11.000,
					})
					
					Interactables.btext = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 4, 0, 3),
						Size = UDim2.new(0, 15, 0, 15),
						ZIndex = 2,
						Font = Enum.Font.GothamBold,
						Text = "B:",
						Name = "Colorpicker",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 14.000,
					})
					
					Interactables.sback = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(46, 46, 54),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.0469999984, 0, 0, 10),
						Size = UDim2.new(0, 140, 0, 140),
						ZIndex = 2,
						Image = "rbxassetid://4695575676",
						ImageColor3 = Color3.fromRGB(46, 46, 54),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(128, 128, 128, 128),
						SliceScale = 0.040,
					})
					
					Interactables.sat = Library:Create("ImageButton", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BorderColor3 = Color3.fromRGB(221, 221, 221),
						BorderSizePixel = 0,
						Size = UDim2.new(0, 140, 0, 140),
						AutoButtonColor = false,
						Image = "http://www.roblox.com/asset/?id=5113592272",
						ImageColor3 = Color3.fromRGB(255, 0, 0),
					})
					
					Interactables.light = Library:Create("ImageLabel", {
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Size = UDim2.new(1, 0, 1, 0),
						Image = "http://www.roblox.com/asset/?id=5113600420",
					})
					
					Interactables.ring = Library:Create("ImageLabel", {
						AnchorPoint = Vector2.new(0.5, 0.5),
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 140, 0, 0),
						Size = UDim2.new(0, 10, 0, 10),
						SizeConstraint = Enum.SizeConstraint.RelativeYY,
						ZIndex = 5,
						Image = "rbxassetid://244221613",
						ImageColor3 = Color3.fromRGB(0, 0, 0),
					})
					
					Interactables.rainbowback = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(46, 46, 54),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0, 160, 0, 10),
						Size = UDim2.new(0, 20, 0, 140),
						ZIndex = 2,
						Image = "rbxassetid://4695575676",
						ImageColor3 = Color3.fromRGB(46, 46, 54),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(128, 128, 128, 128),
						SliceScale = 0.040,
					})
					
					Interactables.rainbow = Library:Create("ImageButton", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Size = UDim2.new(0, 20, 0, 140),
						Image = "http://www.roblox.com/asset/?id=5118428654",
					})
					
					Interactables.rainbowlocation = Library:Create("Frame", {
						BackgroundColor3 = Color3.fromRGB(23, 23, 23),
						BorderSizePixel = 0,
						Size = UDim2.new(0, 20, 0, 2),
					})
					
					Interactables.rainbowtoggle = Library:Create("ImageButton", {
						Active = false,
						BackgroundColor3 = Color3.fromRGB(248, 248, 248),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0.0529999994, 0, 0, 180),
						Selectable = false,
						Size = UDim2.new(0, 172, 0, 20),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(29, 29, 35),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.rainbowtoggletext = Library:Create("TextLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						Position = UDim2.new(0, 1, 0, 2),
						Size = UDim2.new(-0.529476523, 200, 0, 16),
						Font = Enum.Font.GothamBold,
						Text = "Rainbow",
						Name = "Colorpicker",
						TextColor3 = Color3.fromRGB(255, 255, 255),
						TextSize = 14.000,
						TextXAlignment = Enum.TextXAlignment.Left,
					})
					
					Interactables.rainbowtoggleback = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0, 118, 0, 0),
						Size = UDim2.new(0, 50, 0, 16),
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(20, 20, 20),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					Interactables.rainbowtoggleonoff = Library:Create("ImageLabel", {
						BackgroundColor3 = Color3.fromRGB(255, 255, 255),
						BackgroundTransparency = 1.000,
						BorderSizePixel = 0,
						Position = UDim2.new(0, 2, 0, 2),
						Size = UDim2.new(0, 20, 0, 12),
						ZIndex = 2,
						Image = "rbxassetid://3570695787",
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(100, 100, 100, 100),
						SliceScale = 0.040,
					})
					
					
					Interactables.colorpickerframeb.Parent = Main.Motherframe
					Interactables.colorpickerframe.Parent = Interactables.colorpickerframeb
					Interactables.colorpickerupline.Parent = Interactables.colorpickerframe
					Interactables.colorpickeruplinegradient.Parent = Interactables.colorpickerupline
					Interactables.rback.Parent = Interactables.colorpickerframe
					Interactables.rtext.Parent = Interactables.rback
					Interactables.rvalue.Parent = Interactables.rback
					Interactables.gback.Parent = Interactables.colorpickerframe
					Interactables.gtext.Parent = Interactables.gback
					Interactables.gvalue.Parent = Interactables.gback
					Interactables.bback.Parent = Interactables.colorpickerframe
					Interactables.btext.Parent = Interactables.bback
					Interactables.bvalue.Parent = Interactables.bback
					Interactables.sback.Parent = Interactables.colorpickerframe
					Interactables.sat.Parent = Interactables.sback
					Interactables.light.Parent = Interactables.sat
					Interactables.ring.Parent = Interactables.sat
					Interactables.rainbowback.Parent = Interactables.colorpickerframe
					Interactables.rainbow.Parent = Interactables.rainbowback
					Interactables.rainbowlocation.Parent = Interactables.rainbow
					Interactables.rainbowtoggle.Parent = Interactables.colorpickerframe
					Interactables.rainbowtoggletext.Parent = Interactables.rainbowtoggle
					Interactables.rainbowtoggleback.Parent = Interactables.rainbowtoggletext
					Interactables.rainbowtoggleonoff.Parent = Interactables.rainbowtoggleback
					
					
					Section.Container.Size = Section.Container.Size + UDim2.new(0, 0, 0, 45)
					Category.Container.CanvasSize = Category.Container.CanvasSize + UDim2.new(0, 0, 0, 45)
					
					Interactables.colorpickerb.Parent = Section.Container
					Interactables.colorpickertext.Parent = Interactables.colorpickerb
					Interactables.colorpickerbutton.Parent = Interactables.colorpickerb
					
					Interactables.colorpickerb.MouseButton1Click:Connect(function()
						colorpickeropen = not colorpickeropen
						
						for i,v in pairs(Main.Motherframe:GetChildren()) do
							if v.Name == "colorframe" then
								game:GetService("TweenService"):Create(v, TweenInfo.new(0.3), {Size = UDim2.new(0, 0, 0, 205)}):Play()
							end
						end
						
						if colorpickeropen then 
							game:GetService("TweenService"):Create(Interactables.colorpickerframeb, TweenInfo.new(0.3), {Size = UDim2.new(0, 190, 0, 205)}):Play()
						end
					end)
					
					
					local colorbase = Color3.new(1,0,0)
					colorpickervalue = colorbase
					local Saturation = 1
					local Darkness = 0
					local colourPickColour = colorbase
					
					local function UpdateColorPicker()
						
						colourPickColour = colorbase
						
						if Darkness == 1 then
							colourPickColour = Color3.new(0,0,0)
							return
						end
						
						if Saturation < 1 then
							local r = math.clamp(1 + (colourPickColour.r - 1) * Saturation, 0, 1)
							local g = math.clamp(1 + (colourPickColour.g - 1) * Saturation, 0, 1)
							local b = math.clamp(1 + (colourPickColour.b - 1) * Saturation, 0, 1)
							colourPickColour = Color3.new( r, g, b )
						end
						
						if Darkness > 0 then 
							local r = math.clamp(colourPickColour.r * (1 - Darkness ), 0, 1)
							local g = math.clamp(colourPickColour.g * (1 - Darkness ), 0, 1)
							local b = math.clamp(colourPickColour.b * (1 - Darkness ), 0, 1)
							colourPickColour = Color3.new(r,g,b)
						end
						
						Interactables.rvalue.Text = tostring(math.floor(colourPickColour.r * 255))
						Interactables.gvalue.Text = tostring(math.floor(colourPickColour.g * 255))
						Interactables.bvalue.Text = tostring(math.floor(colourPickColour.b * 255))
						
						local rv = tonumber(Interactables.rvalue.Text)
						local gv = tonumber(Interactables.gvalue.Text)
						local bv = tonumber(Interactables.bvalue.Text)
						
						
						print(colorpickervalue)
						colorpickervalue = Color3.fromRGB(math.floor(colourPickColour.r * 255),math.floor(colourPickColour.g * 255),math.floor(colourPickColour.b * 255))
						
						Interactables.colorpickerbutton.ImageColor3 = colourPickColour
						
						if CallBack then
							CallBack(colorpickervalue)
						end
					end
					
					if Others then
						if Others.default then
							local r,g,b = math.floor(Others.default.r * 255),math.floor(Others.default.g * 255),math.floor(Others.default.b * 255)
							colorbase = Color3.fromRGB(r,g,b)
							Interactables.sat.ImageColor3 = colorbase
							wait(.2)
							UpdateColorPicker()
						end
					end
					
					local function setPickerColor(y)
						local rY = y - Interactables.rainbow.AbsolutePosition.Y;
						local cY = math.clamp(rY, 0, Interactables.rainbow.AbsoluteSize.Y - Interactables.rainbowlocation.AbsoluteSize.Y);
						local offset = (y - Interactables.rainbow.AbsolutePosition.Y) - Interactables.rainbowlocation.AbsoluteSize.Y
						local scale = offset / Interactables.rainbow.AbsoluteSize.Y
						TS:Create(Interactables.rainbowlocation, TweenInfo.new(0.1), {Position = UDim2.new(0, 0, 0, cY)}):Play()
						local color = Color3.fromHSV(math.clamp(scale, 0, 1), 1, 1)
						local r,g,b = math.floor(color.r * 255), math.floor(color.g * 255), math.floor(color.b * 255)
						colorbase = Color3.fromRGB(r,g,b)
						
						Interactables.sat.ImageColor3 = colorbase
						UpdateColorPicker()
					end
					
					local function setPickerLight(x,y)
						Saturation = x / 140
						Darkness = y / 140
						
						TS:Create(Interactables.ring, TweenInfo.new(0.1), {Position = UDim2.new(0, x, 0, y)}):Play()
						
						UpdateColorPicker()
					end
					
					local rc
					local cc
					
					UIS.InputEnded:Connect(function(Mouse)
						if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
							if(cc) then
								cc:Disconnect()
								cc = nil
							end
							if(rc) then 
								rc:Disconnect()
								rc = nil
							end
						end
					end)
					
					local rainbow = false
					
					Interactables.rainbow.MouseButton1Down:Connect(function()
						if not rainbow then 
							rc = game:GetService("RunService").Heartbeat:Connect(function()
								setPickerColor(mouse.Y)
							end)
						end
					end)
					
					Interactables.sat.MouseButton1Down:Connect(function()
						cc = game:GetService("RunService").Heartbeat:Connect(function()
							local v = game:GetService("GuiService"):GetGuiInset()
							local y = math.clamp(mouse.Y - Interactables.sat.AbsolutePosition.Y - v.y + 34, 0, 140 )
							local x = math.clamp(mouse.X - Interactables.sat.AbsolutePosition.X - v.x, 0, 140 )
							setPickerLight(x,y)
						end)
					end)
					
					local function zigzag(X) return math.acos(math.cos(X*math.pi))/math.pi end
					Interactables.rainbowtoggle.MouseButton1Click:Connect(function()
						rainbow = not rainbow
						if rainbow then 
							game:GetService("TweenService"):Create(Interactables.rainbowtoggleonoff, TweenInfo.new(0.1), {Position = UDim2.new(0, 28,0, 2)}):Play()
							local counter = 0
							repeat wait() 
								local color = Color3.fromHSV(zigzag(counter),1,1)
								local r = color.r * 255
								local b = color.b * 255
								local g = color.g * 255
								if counter >= 1.01 then
									counter = -0.05
								end
								colorbase = Color3.fromRGB(r,g,b)
								game:GetService("TweenService"):Create(Interactables.rainbowlocation, TweenInfo.new(0.1), {Position = UDim2.new(0, 0, counter, 0)}):Play()
								counter = counter + 0.01
								Interactables.sat.ImageColor3 = colorbase
								UpdateColorPicker()
							until rainbow == false
						else
							game:GetService("TweenService"):Create(Interactables.rainbowtoggleonoff, TweenInfo.new(0.1), {Position = UDim2.new(0, 2,0, 2)}):Play()
						end
					end)
					
				end

				function Library:SetThemeColor(Theme, Color)
					Themes[Theme] = Color
				end 

				return Interactables
				
			end
			
			Section.Container.Parent = Category.Container
			
			Section.SectionPadding.Parent = Section.Container
			
			Section.SectionLayout.Parent = Section.Container
			
			Section.SectionName.Parent = Section.Container
			
			return Section
			
		end
		
		CategoryDistanceCounter = CategoryDistanceCounter + 35
		
		Category.CButton.Parent = Main.Sidebar
		
		Category.Container.Parent = Main.Categorieshandler
		
		Category.CPadding.Parent = Category.Container
		
		Category.CLayout.Parent = Category.Container
		
		Main.Sidebar.CanvasSize = Main.Sidebar.CanvasSize + UDim2.new(0, 0, 0, 35)
		
		firstCategory = false
		
		return Category
		
	end
	
	Main.Screengui.Parent = game:GetService("CoreGui")
	Main.Motherframe.Parent = Main.Screengui
	Main.Upline.Parent = Main.Motherframe
	Main.Uplinegradient.Parent = Main.Upline
	Main.Sidebar.Parent = Main.Motherframe
	Main.Categorieshandler.Parent = Main.Motherframe
	Main.Categoriesselector.Parent = Main.Sidebar
	
	return Main
end

return Library
