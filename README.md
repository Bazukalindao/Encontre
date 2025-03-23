local function createESP(part)
    if part:IsDescendantOf(game.Players.LocalPlayer.Character) then
        return
    end

    local esp = Instance.new("BoxHandleAdornment")
    esp.Size = part.Size + Vector3.new(0.2, 0.2, 0.2)
    esp.Adornee = part
    esp.Color3 = Color3.fromRGB(0, 0, 0)
    esp.Transparency = 0.3
    esp.AlwaysOnTop = true
    esp.ZIndex = 5
    esp.Parent = game.CoreGui
end

local function findButtons()
    for _, v in pairs(workspace:GetDescendants()) do
        if v:IsA("ProximityPrompt") then
            local parentPart = v.Parent:IsA("BasePart") and v.Parent or v.Parent:FindFirstChildOfClass("BasePart")
            if parentPart and not parentPart:IsDescendantOf(game.Players.LocalPlayer.Character) then
                createESP(parentPart)
            end
        end
    end
end

findButtons()

workspace.DescendantAdded:Connect(function(obj)
    if obj:IsA("ProximityPrompt") then
        local parentPart = obj.Parent:IsA("BasePart") and obj.Parent or obj.Parent:FindFirstChildOfClass("BasePart")
        if parentPart and not parentPart:IsDescendantOf(game.Players.LocalPlayer.Character) then
            createESP(parentPart)
        end
    end
end)
