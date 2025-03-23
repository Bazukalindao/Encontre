local function createESP(part)
    if part and part:IsA("BasePart") then
        local esp = Instance.new("BoxHandleAdornment")
        esp.Size = part.Size + Vector3.new(0.1, 0.1, 0.1)
        esp.Adornee = part
        esp.Color3 = Color3.fromRGB(255, 0, 0)
        esp.Transparency = 0.3
        esp.AlwaysOnTop = true
        esp.ZIndex = 5
        esp.Parent = game.CoreGui
    end
end

local function findButtons()
    for _, v in pairs(workspace:GetDescendants()) do
        if v:IsA("BasePart") and v.Name:lower():find("button") then
            createESP(v)
        end
    end
end

findButtons()

workspace.DescendantAdded:Connect(function(obj)
    if obj:IsA("BasePart") and obj.Name:lower():find("button") then
        createESP(obj)
    end
end)
