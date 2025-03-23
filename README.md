local function createESP(part)
    local esp = Instance.new("BoxHandleAdornment")
    esp.Size = part.Size + Vector3.new(0.1, 0.1, 0.1)
    esp.Adornee = part
    esp.Color3 = Color3.fromRGB(0, 255, 0)
    esp.Transparency = 0.3
    esp.AlwaysOnTop = true
    esp.ZIndex = 5
    esp.Parent = game.CoreGui
end

local function findButtons()
    for _, v in pairs(workspace:GetDescendants()) do
        if v:IsA("BasePart") and (v.Name:lower():find("button") or v.Name:lower():find("botão") or v.Name:lower():find("click")) then
            createESP(v)
        end
    end
end

findButtons()

workspace.DescendantAdded:Connect(function(obj)
    if obj:IsA("BasePart") and (obj.Name:lower():find("button") or obj.Name:lower():find("botão") or obj.Name:lower():find("click")) then
        createESP(obj)
    end
end)
