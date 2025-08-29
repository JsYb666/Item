local Library = {

	ObjectsFolder = Instance.new("Folder"),
	ScreenGui = Instance.new("ScreenGui"),
	HighlightsFolder = Instance.new("Folder"),
	BillboardsFolder = Instance.new("Folder"),
	TracersFrame = Instance.new("Frame"),
	Highlights = {},
	Labels = {},
	Elements = {},
	ElementsEnabled = {},
	Frames = {},
	TotalObjects = {},
	TransparencyEnabled = {},
	Connections = {},
	Billboards = {},
	ColorTable = {},
	TextTable = {},
	Lines = {},
	Font = Enum.Font.Oswald,
	ConnectionsTable = {},
	Objects = {},
	ConnectionsManager = {},
	TracerTable = {},
	HighlightNames = {},
	HighlightedObjects = {},
	RemoveIfNotVisible = true,
	Rainbow = false,
	UseBillboards = false,
	Tracers = false,
	Bold = false,
	Unloaded = false,
	ShowDistance = false,
	MatchColors = true,
	TextTransparency = 0,
	TracerOrigin = "Bottom",
	FillTransparency = 0.75,
	OutlineTransparency = 0,
	TextOffset = 0,
	TextOutlineTransparency = 0,
	FadeTime = 0,
	TracerSize = 0.5,
	TextSize = 20,
	DistanceSizeRatio = 1,
	OutlineColor = Color3.fromRGB(255,255,255),
	RainbowColor = Color3.fromRGB(255,255,255)
}



local RainbowTable = {
	HueSetup = 0,
	Hue = 0,
	Step = 0,
	Color = Color3.new(),
	Enabled = false,


}



ObjectsFolder = Library.ObjectsFolder
HttpService = game:GetService("HttpService")
HighlightedObjects = Library.HighlightedObjects
Highlights = Library.Highlights
ConnectionsTable = Library.ConnectionsTable
Objects = Library.Objects
TotalObjects = Library.TotalObjects
Billboards = Library.Billboards
Frames = Library.Frames
ScreenGui = Library.ScreenGui

HighlightsFolder = Library.HighlightsFolder
Labels = Library.Labels
Connections = Library.Connections
Elements = Library.Elements
TextTable = Library.TextTable
Players = game:GetService("Players")
CoreGui = (identifyexecutor ~= nil and game:GetService("CoreGui") or Players.LocalPlayer.PlayerGui)

RunService = game:GetService("RunService")
TweenService = game:GetService("TweenService")
GetHUI = (CoreGui:FindFirstChild("RobloxGui") or CoreGui);
ColorTable = Library.ColorTable
ScreenGui.Parent = GetHUI
TracersFrame = Library.TracersFrame
HighlightsFolder.Parent = ScreenGui
BillboardsFolder = Library.BillboardsFolder
BillboardsFolder.Parent = ScreenGui

ScreenGui.ResetOnSpawn = false
ScreenGui.IgnoreGuiInset = true

TracersFrame.Size = UDim2.new(1,0,1,0)
TracersFrame.BackgroundTransparency = 1

TracersFrame.Parent = ScreenGui

Camera = workspace.CurrentCamera




-- Functions --

function Library:GenerateRandomString()

	--"abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890{}[]<>/#@?!()"
	
	local Characters = "1234567890abcdef"
	local RandomString = ""


	local function GenerateSegment()

		local Result = {}
		local RandomNumber = math.random(9,11)
		for i = 1, RandomNumber do

			local RandomIndex = math.random(1, #Characters)
			table.insert(Result, Characters:sub(RandomIndex, RandomIndex))
		end
		return table.concat(Result)
	end

	local Segment1 = GenerateSegment() .. "-"
	local Segment2 = GenerateSegment() .. "-"
	local Segment3 = GenerateSegment() .. "-"
	local Segment4 = GenerateSegment() .. "-"
	local Segment5 = GenerateSegment() .. "-"
	local Segment6 = GenerateSegment()
	RandomString = Segment1 .. Segment2 .. Segment3 .. Segment4 .. Segment5 .. Segment6
	return RandomString

end


if Library.Unloaded == true then return end
function Library:AddESP(Parameters)
	local Object = Parameters.Object

	if Library.ElementsEnabled[Object] == true or Library.Unloaded == true then return end
	
	if not Object:IsA("BasePart") and not Object:IsA("Model") then
		return
	end





	Library.TransparencyEnabled[Object] = false
	
	

	if Highlights[Object] then
		Highlights[Object]:Destroy()
		Highlights[Object] = nil
	end



	local MainPart = nil
	if Parameters.BasePart then
		MainPart = Parameters.BasePart
	end

	local highlight = Instance.new("Highlight")
	highlight.FillTransparency = 1
	highlight.OutlineTransparency = 1
	highlight.Name = Library.HighlightNames[Object] or Library:GenerateRandomString()
	highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
	highlight.Parent = HighlightsFolder
	highlight.Adornee = Object
	Highlights[Object] = highlight
	local ObjectTable = {Object}
	TextTable[Object] = Parameters.Text

	local TextFrame = Instance.new("Frame")
	TextFrame.Visible = false
	TextFrame.BackgroundTransparency = 1
	TextFrame.Name = Library:GenerateRandomString()
	TextFrame.Size = UDim2.new(1,0,1,0)
	TextFrame.AnchorPoint = Vector2.new(0.5,0.5)
	TextFrame.Parent = BillboardsFolder
	local TextLabel = Instance.new("TextLabel")
	TextLabel.Name = Library:GenerateRandomString()
	TextLabel.BackgroundTransparency = 1
	TextLabel.Text = Parameters.Text
	TextLabel.TextTransparency = 1
	TextLabel.TextStrokeTransparency = Library.TextOutlineTransparency
	TextLabel.Size = UDim2.new(1,0,1,0)
	TextLabel.Font = Library.Font
	TextLabel.TextSize = Library.TextSize
	TextLabel.RichText = true
	TextLabel.Parent = TextFrame
	TextLabel.TextColor3 = Parameters.Color

	Labels[Object] = TextLabel
	Objects[Object] = ObjectTable




	Library.ElementsEnabled[Object] = true





	Labels[Object] = TextLabel

	Library.HighlightNames[Object] = Library:GenerateRandomString()

if Library.ConnectionsTable[Object] == nil then
	Library.ConnectionsManager[Object] = {}
	end


local Manager = Library.ConnectionsManager[Object]

if highlight then
		TweenService:Create(highlight,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{FillTransparency = Library.FillTransparency}):Play()
		TweenService:Create(highlight,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{OutlineTransparency = Library.OutlineTransparency}):Play()
end

	





	Frames[Object] = TextFrame
	Labels[Object] = TextLabel

	Objects[Object] = Object
	ColorTable[Object] = Parameters.Color 
	
	local lineFrame = Instance.new("Frame")
	lineFrame.Size = UDim2.new(0,0,0,0)
	lineFrame.BackgroundTransparency = 1
	lineFrame.AnchorPoint = Vector2.new(0.5, 0.5)
	lineFrame.Parent = TracersFrame
	lineFrame.Name = Library:GenerateRandomString()
	local stroke = Instance.new("UIStroke")
	stroke.Thickness = Library.TracerSize
	stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	stroke.Parent = lineFrame
	stroke.Transparency = 1
	
	TweenService:Create(lineFrame,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{BackgroundTransparency = 0}):Play()


	TweenService:Create(stroke,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{Transparency = 0}):Play()
	
	Library.Lines[Object] = {lineFrame, stroke}


	

	if TextLabel then
		local Tween = TweenService:Create(TextLabel,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{TextTransparency = Library.TextTransparency})
		Tween:Play()
		TweenService:Create(TextLabel,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{TextStrokeTransparency = Library.TextOutlineTransparency}):Play()
		local TweenConnection = Tween.Completed:Connect(function()
			Library.TransparencyEnabled[Object] = true
			
		end)
		table.insert(Manager, TweenConnection)
	end
	
	




	table.insert(Elements,TextFrame)
	table.insert(TotalObjects, Object)




	local Destroying1 = Object:GetPropertyChangedSignal("Parent"):Connect(function()
		Library:RemoveESP(Object)
		
	end)
	table.insert(Manager, Destroying1)
	if Object.Parent ~= nil then
		local Destroying2 = Object.Parent:GetPropertyChangedSignal("Parent"):Connect(function()
			Library:RemoveESP(Object)
			


		end)
		table.insert(Manager, Destroying2)
	end
	if Object:IsA("Model") and Object.PrimaryPart then
		local Destroying3 = Object.PrimaryPart:GetPropertyChangedSignal("Parent"):Connect(function()
			Library:RemoveESP(Object)
			
		end)
		table.insert(Manager, Destroying3)
	end
	
	
	
	

end

function Library:SetColorTable(Name,Color)
	ColorTable[Name] = Color
end

function Library:SetFadeTime(Number)
	Library.FadeTime = Number
end

function Library:SetTextTransparency(Number)
	Library.TextTransparency = Number
	for i,Label in pairs(Labels) do
		Label.TextTransparency = Number
	end
end

function Library:SetFillTransparency(Number)
	Library.FillTransparency = Number
	for i,Highlight in pairs(Highlights) do
		if Highlight:IsA("Highlight") then
			Highlight.FillTransparency = Number
		end
	end
end

function Library:SetOutlineTransparency(Number)
	Library.OutlineTransparency = Number
	for i,Highlight in pairs(Highlights) do
		if Highlight:IsA("Highlight") then
			Highlight.OutlineTransparency = Number
		end
	end
end

function Library:SetTextSize(Number)
	Library.TextSize = Number
	for i,Label in pairs(Labels) do
		Label.TextSize = Number
	end
end
function Library:SetTextOutlineTransparency(Number)
	Library.TextOutlineTransparency = Number
	for i,Label in pairs(Labels) do
		Label.TextStrokeTransparency = Number
	end
end
function Library:SetFont(Font)
	Library.Font = Font
	for i,Label in pairs(Labels) do
		Label.Font = Font
	end
end

function Library:UpdateObjectText(Object,Text)
	if Labels[Object] then
		TextTable[Object] = Text
	end
end
function Library:UpdateObjectColor(Object,Color)
	ColorTable[Object] = Color
	if Labels[Object] then
		Labels[Object].TextColor3 = Color
	end

end

function Library:SetOutlineColor(Color)
	Library.OutlineColor = Color
end

function Library:SetRainbow(Value)
	Library.Rainbow = Value
end

function Library:SetShowDistance(Value)
	Library.ShowDistance = Value
end

function Library:SetMatchColors(Value)
	Library.MatchColors = Value
end

function Library:SetTracers(Value)
	Library.Tracers = Value
	TracersFrame.Visible = Value
end

function Library:SetTracerOrigin(Value)
	Library.TracerOrigin = Value
end

function Library:SetDistanceSizeRatio(Value)
	Library.DistanceSizeRatio = Value
end

function Library:SetTracerSize(Value)
	Library.TracerSize = 0.5 * Value
end




function removeObjectFromTables(object)
	for index, obj in pairs(TotalObjects) do

		if obj == object then

			table.remove(TotalObjects, index)

			break
		end

	end
end


function Library:RemoveESP(Object)
	if Library.Unloaded == true or Library.ElementsEnabled[Object] ~= true then return end

	Library.ElementsEnabled[Object] = false


	Library.TransparencyEnabled[Object] = false




	local Value = Instance.new("Frame", game.ReplicatedStorage)
	Value.BackgroundTransparency = 0
	Value.Name = Library:GenerateRandomString()
	
	game:GetService("Debris"):AddItem(Value, Library.FadeTime + 0.5)


	local TextFrame = Frames[Object]

	local Manager = Library.ConnectionsManager[Object]
	for i,Connection in pairs(Manager) do
		if Connection ~= nil then
			Connection:Disconnect()
		end
	end



	local TextLabel = Labels[Object]

	if TextLabel then
		TweenService:Create(TextLabel,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{TextTransparency = 1}):Play()

	end
	


	if Library.Lines[Object] ~= nil then
		if Library.Lines[Object][1] ~= nil  then
			TweenService:Create(Library.Lines[Object][1],TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{BackgroundTransparency = 1}):Play()
		end
		if Library.Lines[Object][2] ~= nil  then
			TweenService:Create(Library.Lines[Object][2],TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{Transparency = 1}):Play()
		end

	end

	local Highlight
	if Highlights[Object] then

		TweenService:Create(Highlights[Object],TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{FillTransparency = 1}):Play()
		TweenService:Create(Highlights[Object],TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{OutlineTransparency = 1}):Play()
		Highlight = Highlights[Object]

	end

	if Library.Lines[Object][2] ~= nil then
		TweenService:Create(Library.Lines[Object][2] ,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{Transparency = 1}):Play()

	end

	if Object.Parent == nil then
		if Library.ElementsEnabled[Object] == false then

			if Frames[Object] then
				Frames[Object]:Destroy()
				Frames[Object] = nil
			end
			Objects[Object] = nil



			if Highlight then
				Highlight:Destroy()
				Highlights[Object] = nil

			end
			
			

			removeObjectFromTables(Object)

			if Library.Lines[Object] ~= nil then
				if Library.Lines[Object][1] ~= nil  then
					Library.Lines[Object][1]:Destroy()
				end
				if Library.Lines[Object][2] ~= nil  then
					Library.Lines[Object][2]:Destroy()
				end
				Library.Lines[Object] = {}
			end

			if Library.TracerTable[Object] ~= nil then
				Library.TracerTable[Object]:Destroy()

			end





			Value:Destroy()
		else
			if Highlight then
				TweenService:Create(Highlight,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{FillTransparency = Library.FillTransparency}):Play()
				TweenService:Create(Highlight,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{OutlineTransparency = Library.OutlineTransparency}):Play()
			end

		end

	else
		local DestroyTween = TweenService:Create(Value,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{BackgroundTransparency = 1})
		DestroyTween:Play()





		local DestroyTween1 = DestroyTween.Completed:Connect(function()
			if Library.ElementsEnabled[Object] == false then

				if Frames[Object] then
					Frames[Object]:Destroy()
					Frames[Object] = nil
				end

				removeObjectFromTables(Object)

				if Highlight then
					Highlight:Destroy()
					Highlights[Object] = nil

				end




				if Library.Lines[Object] ~= nil then
					if Library.Lines[Object][1] ~= nil  then
						Library.Lines[Object][1]:Destroy()
					end
					if Library.Lines[Object][2] ~= nil  then
						Library.Lines[Object][2]:Destroy()
					end
					Library.Lines[Object] = {}
				end

				if Library.TracerTable[Object] ~= nil then
					Library.TracerTable[Object]:Destroy()

				end





				Value:Destroy()
			else
				if Highlight then
					TweenService:Create(Highlight,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{FillTransparency = Library.FillTransparency}):Play()
					TweenService:Create(Highlight,TweenInfo.new(Library.FadeTime,Enum.EasingStyle.Quad),{OutlineTransparency = Library.OutlineTransparency}):Play()
				end

			end
		end)
		table.insert(Manager, DestroyTween1)
	end
end






ElementsConnection = RunService.RenderStepped:Connect(function()
	





	for _, object in ipairs(TotalObjects) do
		
		if not object:IsDescendantOf(workspace) then Library:RemoveESP(object) continue end

		local pos
	
				pos = object:GetPivot().Position
		
		
		if pos then

		local screenPoint, onScreen = Camera:WorldToViewportPoint(pos)
			
		local frame = Frames[object]
		local label = Labels[object]
		local highlight = Highlights[object]

			if Library.Lines[object][1] then
				Library.Lines[object][1].Visible = (onScreen)
			end
			
			if frame then frame.Visible = onScreen end
			if not onScreen then
			-- Hide tracers/highlights without destroying
			if highlight then highlight:Destroy() Highlights[object] = nil highlight = nil end
			
			
			continue
		end

		-- Position text label
		if frame then
			frame.Position = UDim2.new(0, screenPoint.X, 0, screenPoint.Y)
		end

		-- Update label content
		local distance = math.round(Players.LocalPlayer:DistanceFromCharacter(pos))
		local distanceText = Library.ShowDistance and ("\n" .. '<font size="' .. math.round(Library.TextSize * Library.DistanceSizeRatio) .. '">[' .. distance .. ']</font>') or ""
		label.Text = TextTable[object] .. distanceText
		
	
		
		
		
		-- Highlight setup
		if Library.ElementsEnabled[object] == true then
			if not highlight then
			
			highlight = Instance.new("Highlight")
			highlight.FillTransparency = 1
			highlight.OutlineTransparency = 1
			highlight.Name = Library.HighlightNames[object] or Library:GenerateRandomString()
			highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
			highlight.Parent = HighlightsFolder
			highlight.Adornee = object
			Highlights[object] = highlight
			end
		end
		
		if highlight then
		

		highlight.Enabled = true
		highlight.FillColor = Library.Rainbow and RainbowTable.Color or ColorTable[object] or Color3.fromRGB(255,255,255)
		highlight.OutlineColor = Library.MatchColors and highlight.FillColor or Library.OutlineColor
			label.TextColor3 = Library.Rainbow and RainbowTable.Color or ColorTable[object] or Color3.fromRGB(255,255,255)
		if Library.TransparencyEnabled[object] == true then
		highlight.FillTransparency = Library.FillTransparency
		highlight.OutlineTransparency = Library.OutlineTransparency
		label.TextTransparency = Library.TextTransparency
		label.TextStrokeTransparency = Library.TextOutlineTransparency
		end
		end
		
		local lineFrame = Library.Lines[object][1]
		local stroke = Library.Lines[object][2]
		local origin = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y * 1)
		
		if Library.TracerOrigin == "Center" then
			local mousePos = game:GetService("UserInputService"):GetMouseLocation();
			origin = Vector2.new(Camera.ViewportSize.X/2,Camera.ViewportSize.Y/2)

		elseif Library.TracerOrigin == "Top" then
			origin = Vector2.new(Camera.ViewportSize.X/2, 0)	
		elseif Library.TracerOrigin == "Mouse" then
			
				origin = Vector2.new(game.Players.LocalPlayer:GetMouse().X,game:GetService("UserInputService"):GetMouseLocation().Y)


		end

		
	

		if not lineFrame then
			lineFrame = Instance.new("Frame")
			lineFrame.Size = UDim2.new(0,1,0,1)
			lineFrame.BackgroundTransparency = 0
			lineFrame.AnchorPoint = Vector2.new(0.5, 0.5)
			lineFrame.Parent = TracersFrame
			lineFrame.Name = Library:GenerateRandomString()
			stroke = Instance.new("UIStroke")
			
			stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
			stroke.Parent = lineFrame
			stroke.Transparency =  0
			Library.Lines[object] = {lineFrame, stroke}
			
		end
		
		if lineFrame and highlight and Library.Tracers == true and onScreen then

		local destination = Vector2.new(screenPoint.X, screenPoint.Y)
		local position = (origin + destination) / 2
		local rotation = math.deg(math.atan2(destination.Y - origin.Y, destination.X - origin.X))
		local length = (origin - destination).Magnitude

		lineFrame.Position = UDim2.new(0, position.X, 0, position.Y)
		lineFrame.Size = UDim2.new(0, length, 0, 1)
		lineFrame.Rotation = rotation
		lineFrame.BackgroundColor3 = highlight.FillColor
		lineFrame.BorderSizePixel = 0
		stroke.Color = highlight.FillColor
				stroke.Thickness = Library.TracerSize
		lineFrame.Visible = true
		end
		end
	end
end)






ConnectionsTable.RainbowConnection = RunService.RenderStepped:Connect(function(Delta)

	RainbowTable.Step = RainbowTable.Step + Delta

	if RainbowTable.Step >= (1 / 60) then
		RainbowTable.Step = 0

		RainbowTable.HueSetup = RainbowTable.HueSetup + (1 / 400);
		if RainbowTable.HueSetup > 1 then RainbowTable.HueSetup = 0; end;
		RainbowTable.Hue = RainbowTable.HueSetup;
		RainbowTable.Color = Color3.fromHSV(RainbowTable.Hue, 0.8, 1);
			Library.RainbowColor = Color3.fromHSV(RainbowTable.Hue, 0.8, 1);

	end
end)

CameraConnection = workspace:GetPropertyChangedSignal("CurrentCamera"):Connect(function()
	Camera = workspace.CurrentCamera
end)






function Library:Unload()
	for i,Object in pairs(Library.Objects) do

		Library:RemoveESP(Object)
	end

	for i,Connection in pairs(ConnectionsTable) do
		Connection:Disconnect()
	end

	ElementsConnection:Disconnect()
	CameraConnection:Disconnect()



	ScreenGui.Enabled = false
	Library.Unloaded = true


end
-- Finishing Touches --

ObjectsFolder.Name = Library:GenerateRandomString()
ScreenGui.Name = Library:GenerateRandomString()
HighlightsFolder.Name = Library:GenerateRandomString()
TracersFrame.Name = Library:GenerateRandomString()
BillboardsFolder.Name = Library:GenerateRandomString()
if getgenv ~= nil then
	getgenv().ESPLibrary = Library
end

return Library
