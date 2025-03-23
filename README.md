local function createESP(part)
    local esp = Instance.new("BoxHandleAdornment")
    esp.Size = part.Size + Vector3.new(0.2, 0.2, 0.2)
    esp.Adornee = part
    esp.Color3 = Color3.fromRGB(0, 0, 0)
    esp.Transparency = 0.3
    esp.AlwaysOnTop = true
    esp.ZIndex = 5
    esp.Parent = game.CoreGui

    local billboard = Instance.new("BillboardGui")
    billboard.Adornee = part
    billboard.Size = UDim2.new(0, 100, 0, 50)
    billboard.StudsOffset = Vector3.new(0, 2, 0)
    billboard.AlwaysOnTop = true
    billboard.Parent = game.CoreGui

    local textLabel = Instance.new("TextLabel")
    textLabel.Size = UDim2.new(1, 0, 1, 0)
    textLabel.BackgroundTransparency = 1
    textLabel.Text = "BOTÃO"
    textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    textLabel.TextScaled = true
    textLabel.Font = Enum.Font.SourceSansBold
    textLabel.Parent = billboard
end

local function findButtons()
    for _, v in pairs(workspace:GetDescendants()) do
        if v:IsA("ProximityPrompt") then
            local parentPart = v.Parent:IsA("BasePart") and v.Parent or v.Parent:FindFirstChildOfClass("BasePart")
            if parentPart then
                createESP(parentPart)
            end
        end
    end
end

findButtons()

workspace.DescendantAdded:Connect(function(obj)
    if obj:IsA("ProximityPrompt") then
        local parentPart = obj.Parent:IsA("BasePart") and obj.Parent or obj.Parent:FindFirstChildOfClass("BasePart")
        if parentPart then
            createESP(parentPart)
        end
    end
end)
